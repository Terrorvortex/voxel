# Voxel Desktop — Windows build without installing Node.js locally

This project wraps the supplied Voxel HTML app in Electron and uses GitHub Actions to build a Windows installer in the cloud. You do **not** need Node.js on your own PC.

## Build the installer on GitHub

1. Extract this ZIP.
2. Sign in to GitHub and create a **new, private repository** (recommended because this is your app source).
3. Upload the contents of this folder to the repository's root. Make sure `package.json`, `main.js`, `index.html`, and `.github/workflows/build-windows.yml` are at the root / shown paths—not inside an extra nested folder.
4. Open the repository's **Actions** tab. If GitHub asks, enable Actions for the repository.
5. Select **Build Voxel for Windows** on the left, click **Run workflow**, then click the green **Run workflow** button.
6. Wait for the workflow to finish successfully. Open that completed run, scroll to **Artifacts**, and download **Voxel-Windows-Installer**.
7. Extract the downloaded artifact ZIP and run the `.exe` installer.

The workflow also runs automatically when you push a commit to the `main` branch.

## Notes

- This packages the current `index.html` as a desktop window; it does not change your Supabase backend or hosting.
- The app still needs an internet connection for Supabase and the Supabase JS CDN.
- Keep Supabase Row Level Security enabled. Never put a Supabase `service_role` secret in this HTML or desktop package; desktop apps are inspectable by users.
- Windows may show a SmartScreen warning because the installer is unsigned. Only run the installer you built from your own repository.
- The workflow builds a 64-bit Windows installer. The `.exe` is created by GitHub Actions; it is not included in this ZIP yet.
