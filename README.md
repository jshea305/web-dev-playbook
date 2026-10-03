# Web Development Playbook & Client Site Workflows

A central repository for deployment procedures, DNS configurations, hosting setups, and site handover documentation for freelance web development projects.

## Project Quick Checklist

When launching static HTML/CSS client websites, follow this standard deployment sequence:

1. **Repository Setup**: Push local project files to GitHub (`main` branch).
2. **Hosting Deployment**: Import Git repository into Netlify, keep build settings default, and deploy.
3. **Access Configuration**: Ensure Netlify Visitor Access is set from **Private** to **Public**.
4. **Custom Domain & DNS**: Add the custom domain in Netlify and update registrar nameservers to Netlify DNS.
5. **SSL Provisioning**: Verify Let's Encrypt TLS certificate provisions automatically once DNS propagates.

---

## Documentation Index

- [Netlify & Custom Domain DNS Deployment Guide](docs/netlify-dns-deployment-guide.md)
