# Termux quickstart for new-3dvr

This guide walks through unzipping the starter repo on Android via Termux, serving it locally, and pushing it to GitHub.

## Prep storage access

1. Give Termux permission to read your downloads:
   ```bash
   termux-setup-storage
   ```
   Approve the Android prompt. This creates the `~/storage` directories (including `~/storage/downloads`).

## Locate and unzip the project

1. List your downloads to confirm the ZIP filename:
   ```bash
   ls ~/storage/downloads
   ```
   If you use a `Download` folder instead of `downloads`, try:
   ```bash
   ls ~/storage/shared/Download
   ```
2. Create a working directory and unzip:
   ```bash
   mkdir -p ~/projects && cd ~/projects
   unzip ~/storage/downloads/new-3dvr.zip
   ```
   Adjust the path/filename if your ZIP lives elsewhere (e.g., `~/storage/shared/Download/new-3dvr.zip`).

## Serve locally

From the unzipped folder, launch a quick server and open it in the Android browser:
```bash
cd new-3dvr
python -m http.server 8080
```
Visit `http://127.0.0.1:8080` or `http://localhost:8080` in your browser. Run `xdg-open http://127.0.0.1:8080` to auto-open.

## Upload to GitHub

### Web UI (simplest)

1. Go to <https://github.com/new> and create a repo.
2. Click **Add file → Upload files** and drop the contents of your unzipped folder (`index.html`, `README.md`, `js/app.js`, etc.).
3. Commit the upload.

### Git CLI (optional)

Install git and push from Termux:
```bash
pkg install git
cd new-3dvr
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<YOUR_USERNAME>/<REPO_NAME>.git
git branch -M main
git push -u origin main
```
Use a GitHub personal access token when prompted for your password.
