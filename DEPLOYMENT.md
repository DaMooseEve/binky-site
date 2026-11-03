# Publishing binky-ai.co.uk

The public site is hosted by Fasthosts. GitHub Actions uploads the five static
HTML pages over encrypted FTP whenever an approved change reaches `main`.

## One-time Fasthosts setup

1. In the Fasthosts control panel, open the web hosting package for
   `binky-ai.co.uk`.
2. Open its FTP accounts or file transfer settings.
3. Create a dedicated deployment account with access only to this website.
4. Record its FTP username and password. The Fasthosts settings for this site
   show the server as `ftp.fasthosts.co.uk` and the web root as `/htdocs/`.

## One-time GitHub setup

In `DaMooseEve/binky-site`, open **Settings → Secrets and variables → Actions**.

Add these **repository secrets**:

- `FASTHOSTS_FTP_USERNAME`
- `FASTHOSTS_FTP_PASSWORD`

Add these **repository variables**:

- `FASTHOSTS_FTP_SERVER` — `ftp.fasthosts.co.uk`
- `FASTHOSTS_FTP_DIRECTORY` — `/htdocs/`
- `FASTHOSTS_DEPLOY_ENABLED` — set to `true` only after checking the directory

Never commit the FTP password to this repository.

## Publishing and rollback

The workflow runs automatically when one of the five HTML pages changes on
`main`. It can also be run from **Actions → Deploy public website to Fasthosts
→ Run workflow**.

To roll back, revert the website commit on `main` or run the workflow from a
commit containing the earlier pages.

The public sign-in entry links to a separate authenticated diagnostics service.
Deploy its live DNS/TLS first; never upload its code, records, invitation files or
credentials to this public repository or web root.
