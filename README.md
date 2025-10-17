# Ziryab

A professional platform for DJing, Music Production, Mastering & Artist Development.

## 🚀 Quick Start

This is a static website that can be deployed to any static hosting platform. See [DEPLOYMENT.md](DEPLOYMENT.md) for deployment instructions.

### Local Development

```bash
# Run a local server
python3 -m http.server 8080
# or
npx http-server -p 8080
```

Then open http://localhost:8080 in your browser.

## 🔒 Security Best Practices

### Environment Variables & Secrets

**IMPORTANT:** Never commit sensitive information to version control!

- ✅ Use environment variables for API keys, secrets, and credentials
- ✅ Copy `.env.example` to `.env` and fill in your values
- ✅ Keep `.env` files in `.gitignore` (already configured)
- ❌ Never hardcode API keys, passwords, or tokens in code
- ❌ Never commit `.env` files to git

### Secret Management Guidelines

1. **For API Keys and Tokens:**
   - Store in `.env` file (locally)
   - Use your hosting provider's environment variable settings (production)
   - Examples: GitHub Secrets, Vercel Environment Variables, Netlify Environment Variables

2. **For Contact Information:**
   - Use environment variables for email addresses and phone numbers
   - Implement contact forms that don't expose email addresses directly
   - Consider using anti-spam protection

3. **For Social Media Links:**
   - While public, store in configuration files that can be easily updated
   - Use `.env` for easier management across environments

### Reporting Security Issues

If you discover a security vulnerability, please:
- **DO NOT** open a public issue
- Contact the repository maintainers directly
- Provide detailed information about the vulnerability
- Allow reasonable time for the issue to be addressed

### Security Checklist for Developers

- [ ] Review `.gitignore` to ensure secret files are excluded
- [ ] Never commit `.env` files or files containing secrets
- [ ] Use `.env.example` as a template (with dummy values only)
- [ ] Scan code for hardcoded credentials before committing
- [ ] Use HTTPS for all external resources and APIs
- [ ] Keep dependencies updated and audit for vulnerabilities
- [ ] Implement Content Security Policy (CSP) headers when deploying

## 📄 License

All Rights Reserved © 2025 Zeryab زرياب