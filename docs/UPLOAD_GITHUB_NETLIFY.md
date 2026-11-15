# New GitHub repository + Netlify deployment (Windows)

Recommended repository name: `ANN-KOREA/GARD-P2P-Asset-Market`.

## A. Web UI (GitHub CLI not required)

1. Open https://github.com/new, owner **ANN-KOREA**, name **GARD-P2P-Asset-Market**.
2. Set **Private** for source-code confidentiality (Netlify can deploy a public site from a private repo when your integration has access). Leave **Add a README**, **.gitignore** and **license** unchecked because those files are already in this package.
3. Click **Create repository**.
4. Extract `GARD_P2P_Asset_Market_New_Repository_v1.0.zip` to a local directory. **Do not upload the ZIP as one file.**
5. In the new repository choose **uploading an existing file** and upload all extracted files and folders including `js`, `docs`, `scripts`, `tests` and `.github/workflows`. Note: some operating-system upload interfaces hide dotfiles/folders; use Git CLI if the `.github` directory is omitted.
6. Commit to `main`. The repo should contain **`index.html`, `owner.html`, `buyer.html`, `catalog.json`, `netlify.toml` at its root**.

## B. Optional one-command creation from Windows PowerShell

Requires Git (https://git-scm.com/downloads), GitHub CLI (https://cli.github.com/) and authentication (`gh auth login`).

In the extracted project folder, run:

```powershell
powershell -ExecutionPolicy Bypass -File .\scripts\Create-GitHub-Repo-Windows.ps1
```

The PowerShell script creates the **new** `ANN-KOREA/GARD-P2P-Asset-Market` repository and pushes all project files if the repository does not already exist and the account has sufficient permissions. Default visibility: **private**. Use `-Public` to intentionally create a public source repository. It does **not** create the Netlify site or transfer private assets.

## C. Netlify

1. Netlify team dashboard → Add new project → Import an existing project → GitHub.
2. Grant repository access and select `ANN-KOREA/GARD-P2P-Asset-Market`.
3. Build command **empty**, publish directory **`.`**, base directory empty. `netlify.toml` includes these settings.
4. Deploy; verify pages `https://<your-netlify-domain>/`, `/owner.html`, `/buyer.html`.
5. Register your own **public contact email** in `/owner.html` → Settings.
6. Create a real asset in owner local storage, explicitly approve its promo metadata, export `catalog.json`, and commit only that JSON in GitHub. Netlify then performs a new deployment.
7. Use `docs/TESTING.md` and record real-device QA results. Tests not executed remain `NOT_RUN`.

## Note on privacy

**Never commit** owner backup JSON, buyer backup JSON, raw paid ZIPs, customer emails, bank receipts, or unpublished original assets to GitHub (public *or* private), unless there is an independently assessed reason and security plan. The site must read only the approved promotional catalog.
