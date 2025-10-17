# Ziryab Static Site Deployment

This site can be deployed as a static website. Here are some common deployment options:

## 🔒 Security Before Deployment

**CRITICAL SECURITY CHECKS:**

1. ✅ Verify no `.env` files are committed to the repository
2. ✅ Check that all API keys/secrets are stored as environment variables
3. ✅ Review `.gitignore` to ensure it excludes sensitive files
4. ✅ Scan code for hardcoded credentials or sensitive information
5. ✅ Use HTTPS for all deployment URLs

### Environment Variables Setup

Each platform has its own way to set environment variables:

- **Vercel:** Project Settings → Environment Variables
- **Netlify:** Site Settings → Build & Deploy → Environment Variables
- **GitHub Pages:** Use GitHub Secrets for Actions (if using CI/CD)

## Deployment Options

## 1. GitHub Pages
- Commit and push your code to GitHub.
- In your repo settings, enable GitHub Pages (set source to `main` branch or `/docs` folder).
- Your site will be available at `https://<username>.github.io/<repo>/`.

## 2. Vercel
- Go to https://vercel.com and sign in with GitHub.
- Import your repo and deploy. Vercel will auto-detect static sites.
- **Security:** Set environment variables in Project Settings before deploying

## 3. Netlify
- Go to https://netlify.com and sign in with GitHub.
- New site from Git, select your repo, and deploy.
- **Security:** Configure environment variables in Site Settings → Build & Deploy

## 4. Local Preview
You can preview locally with a simple HTTP server:

```
python3 -m http.server 8080
```
Then open http://localhost:8080 in your browser.

---

## 🛡️ Security Recommendations

### After Deployment:

1. **Enable HTTPS:** All modern platforms enable HTTPS by default
2. **Set Security Headers:** Configure CSP, X-Frame-Options, etc.
3. **Regular Updates:** Keep dependencies and frameworks updated
4. **Monitor Access:** Review access logs for suspicious activity
5. **Backup Regularly:** Maintain backups of your site and data

### Custom Domain Security:

- Enable DNSSEC if available
- Use CAA records to restrict certificate authorities
- Configure proper SPF/DKIM records for email

For custom domains, follow the provider's instructions after deployment.
