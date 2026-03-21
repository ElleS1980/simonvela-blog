# Domain Setup: simonvela.com → GitHub Pages

## Step 1: GitHub Pages Settings
1. Go to https://github.com/ElleS1980/simonvela-blog/settings/pages
2. Source: "GitHub Actions" (should already be set)
3. Custom domain: enter `simonvela.com`
4. Check "Enforce HTTPS"

## Step 2: DNS Records at your domain registrar
Add these DNS records for `simonvela.com`:

### A Records (point to GitHub Pages):
```
Type: A    Host: @    Value: 185.199.108.153
Type: A    Host: @    Value: 185.199.109.153
Type: A    Host: @    Value: 185.199.110.153
Type: A    Host: @    Value: 185.199.111.153
```

### CNAME Record (for www subdomain):
```
Type: CNAME    Host: www    Value: elles1980.github.io
```

## Step 3: Add CNAME file
Already handled — GitHub adds it automatically when you set the custom domain.

## Step 4: Wait
- DNS propagation takes 1-48 hours
- HTTPS certificate is auto-provisioned by GitHub (takes ~15 min after DNS)
- Check status at: https://github.com/ElleS1980/simonvela-blog/settings/pages

## Verification
- https://simonvela.com should show the blog
- https://www.simonvela.com should redirect to simonvela.com
