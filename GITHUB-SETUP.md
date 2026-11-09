# YouTube Guide v1.1.5 — New GitHub repository setup

This is a **fresh repository package**, configured for **anticgoldfish/youtube-guide-surfer** on the **main** branch. It includes a new, empty `YouTube-Guide/channels.json`. Do not use it to overwrite a channel library you want to preserve.

## 1. Create and upload the repository with GitHub Desktop

1. Create a new **Public** repository named `youtube-guide-surfer` under account `anticgoldfish` on GitHub. Do not initialize it with a README.
2. Download this ZIP and extract its contents into an empty folder (for example `Documents/YouTube-Guide-Surfer`). The folder root must contain `.github`, `YouTube-Guide`, and `scripts`; do not upload an extra containing folder level.
3. In GitHub Desktop, select **File → Add local repository**, choose that folder, and if prompted select **Create a repository here**.
4. Commit the files as `Initial YouTube Guide website` and use **Publish repository** or push to the new GitHub repository. Check that `main` is the branch.
5. Verify on github.com that `.github/workflows/refresh-and-publish.yml` and `YouTube-Guide/index.html` and `YouTube-Guide/channels.json` exist.

## 2. Activate GitHub Pages

1. Open the new repository → **Settings → Pages**. Set **Build and deployment → Source** to **GitHub Actions**.
2. In **Actions**, open **Refresh YouTube Guide and Publish** and choose **Run workflow** on `main`. The workflow also runs on pushes affecting site or updater files, and approximately every 30 minutes.
3. After a successful run, open **https://anticgoldfish.github.io/youtube-guide-surfer/**. If an old view appears, hard reload with Ctrl+Shift+R.

## 3. Set up keys (never commit them)

- Create a NEW fine-grained GitHub Personal Access Token, restricted to repository `anticgoldfish/youtube-guide-surfer`, **Contents: Read and write**.
- Create a YouTube Data API v3 key in Google Cloud and enable YouTube Data API v3 for that project.
- On the website, click **Add Channel**, enter both keys, then **Save Keys in This Browser**. They are saved only in localStorage on that browser/site origin. They are not included in this ZIP.
- Separately, for GitHub Actions to find videos unattended, add the YouTube key under repository **Settings → Secrets and variables → Actions → New repository secret**, name exactly `YOUTUBE_API_KEY`. GitHub Actions cannot read a key from your personal browser. The workflow's own GitHub token handles scheduled commits.

## 4. Create your first channel

Choose **Add Channel → Create Channel** and make the first channel. It should immediately attempt publication. Check `YouTube-Guide/channels.json` on GitHub and verify it is no longer empty. Check from another browser after deployment. The published JSON uses UTC timestamps and can be consumed by a future Android/Google TV APK.

## Notes

- Repository URLs and owner information are public. **Never commit your GitHub token or API key**.
- The browser uses localStorage, not encrypted secret storage. Other scripts on the same origin can read it, and clearing site data removes saved keys.
- If you want the **Sitcoms 101** channel from the old repository in the new one, migrate the old `channels.json` before creating new channels, rather than replacing it after making changes.
- YouTube discovery is subject to API quotas and video embedding restrictions. Automatic schedules reuse existing videos if new results aren't available.
