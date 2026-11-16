# GitHub setup (simple)
1. Create a PRIVATE repository named KhataPro and upload the contents of the KhataPro folder
   (the files inside it, not the folder itself). Make sure the folder `.github` is uploaded too.
   If your browser hides it, use GitHub Desktop or upload `.github/workflows/build.yml` by
   "Add file > Create new file" with the name `.github/workflows/build.yml`.
2. Open the repository > Actions tab. The "Build KhataPro" workflow starts by itself after the upload.
   You can also press "Run workflow".
3. When it finishes: green tick = success. Open the run and download `KhataPro-debug-apk` from Artifacts.
   Red cross = open the failed step, copy the red error text and send it to Claude.
4. Never upload keystore (.jks) files or passwords. Release signing will be added in the final phase
   using GitHub Secrets.
