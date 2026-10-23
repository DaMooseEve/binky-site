# Publishing binky-ai.co.uk

The public site is hosted by Fasthosts. GitHub Actions uploads the three static
HTML pages over encrypted FTP whenever an approved change reaches `main`.

## One-time Fasthosts setup

1. In the Fasthosts control panel, open the web hosting package for
   `binky-ai.co.uk`.
2. Open its FTP accounts or file transfer settings.
3. Create a dedicated deployment account with access only to this website.
4. Record its FTP username, password, server name and web-root folder. The
   expected server is `ftp.binky-ai.co.uk`; the usual web root is `/htdocs/`,
   but use the folder shown by Fasthosts.

## One-time GitHub setup

In `DaMooseEve/binky-site`, open **Settings → Secrets and variables → Actions**.

Add these **repository secrets**:

- `FASTHOSTS_FTP_USERNAME`
- `FASTHOSTS_FTP_PASSWORD`

Add these **repository variables**:

- `FASTHOSTS_FTP_SERVER` — normally `ftp.binky-ai.co.uk`
- `FASTHOSTS_FTP_DIRECTORY` — normally `/htdocs/`
- `FASTHOSTS_DEPLOY_ENABLED` — set to `true` only after checking the directory

Never commit the FTP password to this repository.

## Publishing and rollback

The workflow runs automatically when one of the three HTML pages changes on
`main`. It can also be run from **Actions → Deploy public website to Fasthosts
→ Run workflow**.

To roll back, revert the website commit on `main` or run the workflow from a
commit containing the earlier pages.
