# Publishing binky-ai.co.uk

The public site is hosted by Fasthosts. GitHub Actions uploads the six static
HTML pages and the signed Android test download over encrypted FTP whenever an approved change reaches `main`.

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

The workflow runs automatically when a page or public download changes on
`main`. It can also be run from **Actions → Deploy public website to Fasthosts
→ Run workflow**.

To roll back, revert the website commit on `main` or run the workflow from a
commit containing the earlier pages.

The public sign-in entry links to a separate authenticated diagnostics service.
Deploy its live DNS/TLS first; never upload its code, records, invitation files or
credentials to this public repository or web root.

The install entry publishes only the generic signed Android APK and its checksum.
Private pairing files, VPN profiles, owner identities and signing private keys
must never enter this repository or web root. Windows/iOS availability remains
explicit on install.html. The workflow verifies the public APK checksum after upload.

4 November 2026 installation entry: the homepage, technical page and sign-in page
link to `install.html`. The Android 0.3.8/code14 APK is the existing signed test
release (Android 8+); SHA-256 is published beside the download. It contains no
pairing profile or installation credentials. Windows/iOS installers and remote
browser account access are explicitly unfinished. Local HTML links and desktop/
390px browser layout checks pass; the workflow checks the public APK hash after
upload. Keep the diagnostics sign-in separate from customer Binky access.
