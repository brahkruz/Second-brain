# 🧠 Second Brain OS

A personal dashboard for tasks, habits, goals, projects, notes, books and shows. It runs free on **GitHub Pages**, and you can install it on your phone's home screen like an app.

Your data is kept in a separate **private** repo, so the app can be public while your notes stay private. Every device you connect reads and writes the same data.

```
second-brain        (public)  → the app, served at https://YOUR-NAME.github.io/second-brain/
second-brain-data   (private) → brain.json, your data
```

---

## Setup (about 10 minutes, one time)

### 1. Put the app on GitHub Pages
1. On github.com, click **+ → New repository**. Name it `second-brain` and make it **Public**. Then click **Create**.
2. Click **uploading an existing file** and drag in every file from this folder: `index.html`, `manifest.webmanifest`, `icon.svg`, the three `icon-*.png` files and this `README.md`. Then click **Commit changes**.
3. In the repo, go to **Settings → Pages**. Under *Build and deployment*, set the source to **Deploy from a branch**, pick the branch **main** and the folder **/ (root)**, and click **Save**.
4. After a minute or so, the app is live at `https://YOUR-NAME.github.io/second-brain/`.

### 2. Make the private data repo
1. Click **+ → New repository** again. Name it `second-brain-data`, make it **Private**, and click **Create**.
2. Leave it empty. The app creates `brain.json` the first time it saves.

### 3. Create an access token (the app's key to your data repo)
1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. **Name:** Second Brain. **Expiration:** choose one; a year is reasonable.
3. **Repository access:** choose **Only select repositories**, then pick `second-brain-data`.
4. **Permissions → Repository permissions → Contents:** choose **Read and write**.
5. Click **Generate token** and copy it. It starts with `github_pat_`.

> This token can only read and write `second-brain-data`. It can't touch your other repos.

### 4. Connect the app
1. Open your app link and tap **⚙︎** in the top right.
2. Enter your GitHub username, `second-brain-data` and the token. Then tap **Connect**.
3. The status pill should say **Synced with GitHub**.

Do step 4 once on each device: your computer, your phone, and so on.

### 5. Add it to your phone's home screen
- **iPhone (Safari):** open the link, tap **Share**, then **Add to Home Screen**.
- **Android (Chrome):** open the link, tap **⋮**, then **Add to Home screen** or **Install app**.

---

## How syncing works
- Every change saves to your device right away. A second or two later it saves to `brain.json` in your private repo, so you can also browse your history in the repo's commits.
- When you switch back to the app, it pulls the latest data, so a change made on your laptop shows up on your phone.
- If you're offline, changes stay on the device and sync once you're back online.
- If you edit on two devices at the same moment, the most recent save wins.

## Changing the app
Edit `index.html` in the `second-brain` repo, either with the ✏️ pencil on github.com or by asking Claude for changes and uploading the new file. Pages updates within about a minute, and your data isn't affected.

## Troubleshooting
| Status pill says | Fix |
|---|---|
| GitHub token rejected | The token expired or was pasted wrong. Make a new one (step 3) and reconnect. |
| Data repo not found / Token lacks access | Check the username and repo name, and make sure the token's repository access includes `second-brain-data` with Contents: Read and write. |
| Offline · saved on this device | You're offline. It will sync when you reconnect. |
