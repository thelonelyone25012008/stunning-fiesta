# Deploy Vite + React App to Netlify

## 1. Build the project

```bash
npm install
npm run build
```

## 2. Deploy to Netlify

### Option 1: Connect GitHub/GitLab repository
- Push your code to a repository (if not already).
- Go to [Netlify](https://app.netlify.com/) and create a new site from Git.
- Set build command: `npm run build`
- Set publish directory: `dist`
- Click "Deploy".

### Option 2: Manual deploy
- Run `npm run build` locally.
- Zip the `dist` folder.
- Go to Netlify > Add new site > Deploy manually.
- Upload the zipped `dist` folder.

## 3. Configuration
- No special configuration is needed for Vite + React.
- If you use client-side routing, add a `_redirects` file in `public/` with:
  ```
  /*    /index.html   200
  ```

## 4. Troubleshooting
- If you see a blank page, check the publish directory and redirects.
- For environment variables, set them in Netlify dashboard.

---

**Enjoy your deployed site!**

## Auto-deploy from GitHub & edit in Codespaces (recommended)

1. Create a GitHub repository and push this project to it (if not already):

```bash
git init
git add .
git commit -m "initial"
git branch -M main
git remote add origin <YOUR_GITHUB_REPO_URL>
git push -u origin main
```

2. In Netlify: create a new site > "Sites" > "Add new site" > "Import from Git" and connect your GitHub repo, or create a site normally and note the Site ID.

3. Create a Netlify personal access token:
  - Go to Netlify > User Settings > Applications > Personal access tokens > New access token
  - Copy the token.

4. In your GitHub repository settings > Secrets and variables > Actions, add two repository secrets:
  - `NETLIFY_AUTH_TOKEN` — the personal access token from Netlify
  - `NETLIFY_SITE_ID` — the Site ID from the Netlify site settings

5. Push to `main`. The workflow at `.github/workflows/netlify-deploy.yml` will run and deploy to Netlify automatically.

6. Edit in Codespaces: in the GitHub repo, click "Code" > "Codespaces" > "Create codespace on main". The devcontainer will run `npm install` for you.

Notes:
- The GitHub Actions workflow uses `netlify-cli` to deploy the `dist` folder produced by `npm run build`.
- Keep `NETLIFY_AUTH_TOKEN` private. Rotate if necessary.
