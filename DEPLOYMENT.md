# Ziryab Static Site Deployment

This site can be deployed as a static website. Here are some common deployment options:

## 1. GitHub Pages
- Commit and push your code to GitHub.
- In your repo settings, enable GitHub Pages (set source to `main` branch or `/docs` folder).
- Your site will be available at `https://<username>.github.io/<repo>/`.

## 2. Vercel
- Go to https://vercel.com and sign in with GitHub.
- Import your repo and deploy. Vercel will auto-detect static sites.

## 3. Netlify
- Go to https://netlify.com and sign in with GitHub.
- New site from Git, select your repo, and deploy.

## 4. Local Preview
You can preview locally with a simple HTTP server:

```
python3 -m http.server 8080
```
Then open http://localhost:8080 in your browser.

---

For custom domains, follow the provider's instructions after deployment.
