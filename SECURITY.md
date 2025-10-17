# Security Policy

## 🔒 Security Commitment

We take the security of the Ziryab project seriously. This document outlines our security practices and how to report vulnerabilities.

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |

## 🛡️ Security Best Practices

### For Developers

#### 1. Never Commit Secrets
- **DO NOT** hardcode API keys, passwords, tokens, or credentials in source code
- **DO NOT** commit `.env` files or any files containing secrets
- **DO** use environment variables for all sensitive configuration
- **DO** use `.env.example` with dummy values as a template

#### 2. Environment Variable Management
```bash
# ✅ GOOD: Using environment variables
const apiKey = process.env.API_KEY;

# ❌ BAD: Hardcoded credentials
const apiKey = "sk_live_1234567890abcdef";
```

#### 3. Dependency Security
- Regularly update dependencies to patch security vulnerabilities
- Use `npm audit` or equivalent tools to scan for known vulnerabilities
- Review dependency licenses and sources

#### 4. Code Review Guidelines
Before committing code, always:
- [ ] Search for patterns like: `password`, `secret`, `api_key`, `token`, `credential`
- [ ] Verify no `.env` files are staged for commit
- [ ] Check that `.gitignore` is properly configured
- [ ] Remove any debug code that might expose sensitive data
- [ ] Ensure HTTPS is used for all external resources

### For Deployment

#### Environment Variables Setup

**Never expose sensitive data in your deployed site!**

##### Vercel
```bash
# In Vercel Dashboard:
# Settings → Environment Variables → Add New
KEY=value
```

##### Netlify
```bash
# In Netlify Dashboard:
# Site Settings → Build & Deploy → Environment Variables
KEY=value
```

##### GitHub Pages (with Actions)
```yaml
# Use GitHub Secrets
# Settings → Secrets and Variables → Actions
# Reference in workflows as: ${{ secrets.KEY_NAME }}
```

#### Security Headers

Configure these headers for production deployments:

```
Content-Security-Policy: default-src 'self' https://cdn.tailwindcss.com https://fonts.googleapis.com https://cdnjs.cloudflare.com; style-src 'self' 'unsafe-inline' https://fonts.googleapis.com https://cdnjs.cloudflare.com; script-src 'self' 'unsafe-inline' https://cdn.tailwindcss.com; font-src 'self' https://fonts.gstatic.com https://cdnjs.cloudflare.com;
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

## 🚨 Reporting a Vulnerability

### How to Report

If you discover a security vulnerability, please follow these steps:

1. **DO NOT** open a public GitHub issue
2. **DO NOT** disclose the vulnerability publicly
3. Email the maintainers directly (check repository for contact)
4. Include the following information:
   - Type of vulnerability
   - Full description of the issue
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if available)

### What to Expect

- **Acknowledgment:** Within 48 hours
- **Assessment:** Within 5 business days
- **Fix Timeline:** Depends on severity
  - Critical: 1-7 days
  - High: 7-30 days
  - Medium: 30-90 days
  - Low: As time permits

### Disclosure Policy

- We follow responsible disclosure practices
- We will credit security researchers (unless they prefer to remain anonymous)
- Public disclosure will happen after a fix is deployed
- We appreciate your patience and cooperation

## 🔍 Security Scanning

### Automated Scans

We recommend using these tools to scan for security issues:

```bash
# Scan for secrets in code
git secrets --scan

# npm security audit
npm audit

# Check for hardcoded credentials
grep -r -i -E "(api[_-]?key|secret|password|token)" .

# Check for exposed .env files
find . -name ".env*" ! -name ".env.example"
```

### Pre-commit Hooks

Consider setting up pre-commit hooks to prevent committing secrets:

```bash
#!/bin/bash
# .git/hooks/pre-commit

# Check for .env files
if git diff --cached --name-only | grep -q "\.env$"; then
    echo "Error: Attempting to commit .env file!"
    exit 1
fi

# Check for common secret patterns
if git diff --cached | grep -i -E "(api[_-]?key|secret.*=|password.*=|token.*=)"; then
    echo "Warning: Potential secret detected in commit!"
    echo "Please review your changes carefully."
    exit 1
fi
```

## 📚 Additional Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CWE Top 25](https://cwe.mitre.org/top25/)
- [GitHub Security Best Practices](https://docs.github.com/en/code-security)
- [Web Security Cheat Sheet](https://cheatsheetseries.owasp.org/)

## 🔄 Updates

This security policy may be updated periodically. Check back regularly for the latest security guidelines.

---

**Last Updated:** 2025-10-17
