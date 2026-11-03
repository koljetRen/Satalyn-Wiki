# Hosting on Cloudflare Pages

The wiki is hosted on **Cloudflare Pages**. Cloudflare Pages is free and can build from a **private** GitHub repository, so this repo stays private. Every push to `main` rebuilds and republishes the site automatically. Until the public launch, **Cloudflare Access** puts the whole site behind an email login so only you can open it.

You only need to do this once. It takes about 15 minutes.

## 1. Create a Cloudflare account

Go to <https://dash.cloudflare.com/sign-up> and sign up (the free plan is enough). You don't need to own a domain name.

## 2. Connect the GitHub repository

1. In the Cloudflare dashboard, open **Workers & Pages** in the left sidebar (under **Compute**).
2. Click **Create application**, choose the **Pages** tab, then click **Connect to Git** (sometimes labelled **Import an existing Git repository**).
3. Click **Connect GitHub**. A GitHub window opens to install the **Cloudflare Workers and Pages** app:
   - Choose your account (`koljetren`).
   - Pick **Only select repositories** and select **satalyn-wiki**.
   - Click **Install & Authorize**.
4. Back in Cloudflare, select **koljetren/satalyn-wiki** and click **Begin setup**.

## 3. Build settings

Fill in **Set up builds and deployments** exactly like this:

| Setting | Value |
| --- | --- |
| Project name | `satalyn-wiki`. This becomes the address `satalyn-wiki.pages.dev`. If the name is taken, Cloudflare suggests another; note it down. |
| Production branch | `main` (Quartz's own docs say `v5`; this repo uses `main`) |
| Framework preset | `None` |
| Build command | `npx quartz plugin install && npx quartz build` |
| Build output directory | `public` |
| Root directory | leave empty |

Leave **Environment variables** empty. Cloudflare reads the Node version (22) from the `.node-version` file in the repo.

Click **Save and Deploy**. The first build takes 2–3 minutes. When it finishes, Cloudflare shows the address, for example `https://satalyn-wiki.pages.dev`.

> [!note] Page dates
> Cloudflare downloads only recent history of the repo, so "last modified" dates on pages may all show the date of the latest commit. If that bothers you, change the build command (**Settings → Build → Build configuration → Edit**) to `git fetch --unshallow && npx quartz plugin install && npx quartz build`.

> [!tip] Preview builds of other branches
> Cloudflare also builds every other branch (such as the `package-…` branches) at addresses like `package-9-site.satalyn-wiki.pages.dev`. Step 5 protects those too. If you'd rather not have them at all, go to **Settings → Build → Branch control** and set **Preview branch** to **None**.

## 4. Set `baseUrl`

Quartz needs the site's address for its sitemap, RSS feed and link previews.

1. Open `quartz.config.yaml` and find the line marked `TODO(hosting)`:

   ```yaml
   # TODO(hosting): replace with the address Cloudflare Pages gives the site, e.g.
   # satalyn-wiki.pages.dev (no https://, no trailing slash). See HOSTING.md, step 4.
   baseUrl: satalyn.example.com
   ```

2. Replace it with the address from step 3, **without** `https://` and without a slash at the end, and delete the two TODO comment lines:

   ```yaml
   baseUrl: satalyn-wiki.pages.dev
   ```

3. Commit to `main` (on GitHub you can edit the file in the browser). Cloudflare rebuilds the site within a few minutes.

If you later add your own domain (Pages project → **Custom domains**), set `baseUrl` to that domain instead.

## 5. Make the site private with Cloudflare Access (until the public launch)

As it stands, anyone who guesses the `pages.dev` address can read the site, **including the folded Secrets callouts and the search index, which contains their full text** (see `BUILD-NOTES.md`). Cloudflare Access adds an email login page in front of the site. It is free for up to 50 users.

### 5a. Turn on Zero Trust (first time only)

1. In the dashboard sidebar, click **Zero Trust**.
2. Choose a team name (anything, e.g. `satalyn`) and pick the **Free** plan. Cloudflare may ask for a payment card even on the free plan; it charges nothing.

### 5b. Protect the preview builds

1. Go back to **Workers & Pages** and open the **satalyn-wiki** project.
2. Go to **Settings → General**, find **Access policy**, and click **Enable**.

This protects the branch preview addresses (`*.satalyn-wiki.pages.dev`). The main `satalyn-wiki.pages.dev` address needs one more step:

### 5c. Protect the main address

1. Open **Zero Trust → Access → Applications**. Cloudflare has already created an application for the previews in step 5b; open it and click **Edit**. (Or click **Add an application → Self-hosted** to make a new one.)
2. Under **Application domain**, make sure there are two entries:
   - Subdomain *empty*, domain `satalyn-wiki.pages.dev`, which is the main site
   - Subdomain `*`, domain `satalyn-wiki.pages.dev`, which covers the previews

   Use your real project name if it differs.
3. Under **Policies**, open the policy (or add one) and set:
   - **Action:** Allow
   - **Include → Selector: Emails →** your email address (add more addresses later for players or readers you trust)
4. Under **Authentication** (or **Login methods**), make sure **One-time PIN** is ticked. That means Cloudflare emails you a 6-digit code; no password needed.
5. Save.

Open `https://satalyn-wiki.pages.dev` in a private browser window to test it. You should see a Cloudflare login page asking for your email. Enter it, type the code from your inbox, and the wiki opens. Any other email address is refused.

### 5d. At the public launch

1. First, move every Secrets callout into `content/private/` (see "Secrets" in `CLAUDE.md`), so secret text is no longer in the built site or its search index.
2. Then delete the Access application in **Zero Trust → Access → Applications**, and turn off **Access policy** in the Pages project's **Settings → General** if you want public previews too.

## Day to day

- **Publishing:** merge or push to `main`. Cloudflare rebuilds automatically; see **Workers & Pages → satalyn-wiki → Deployments** for progress and logs.
- **A build failed:** open the failed deployment and read the build log. The same command run locally (`npm ci`, then `npx quartz plugin install && npx quartz build`) shows the same error.
- **Rolling back:** in **Deployments**, open an older successful deployment and choose **Rollback to this deployment**.
