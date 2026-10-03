# Netlify Deployment & Custom Domain DNS Guide

This guide outlines the standard operating procedure for deploying static client websites from GitHub to Netlify and configuring custom domain DNS records.

---

## 1. Initial Deployment via Netlify

1. Log into **Netlify** and navigate to **Projects**.
2. Click **Import a Git repository** $\rightarrow$ **GitHub**.
3. Authenticate with GitHub (completing GitHub Mobile or 2FA verification if prompted).
4. Select the target repository (e.g., `SLocumJunkSolutions`).
5. Configure project options:
   - **Project Name**: Set custom URL prefix (e.g., `slocumjunksolutions`).
   - **Branch to Deploy**: `main`
   - **Build Settings**: Leave `Base Directory`, `Build Command`, and `Publish Directory` blank (for static HTML/CSS).
6. Click **Deploy [Project Name]**.

---

## 2. Setting Site Access to Public

Netlify defaults new projects to private access. To make the site publicly accessible:

1. Open the project in the Netlify Dashboard.
2. Click the **Make Public** button on the overview banner (or go to **Site Configuration** $\rightarrow$ **Access Control** $\rightarrow$ **Visitor Access**).
3. Confirm access mode is set to **Public**.

---

## 3. Custom Domain & DNS Setup

### Primary Method: Netlify Managed DNS (Recommended)

1. In the Netlify Dashboard, go to **Domain Management**.
2. Click **Add a domain** $\rightarrow$ **Add existing domain**.
3. Enter the custom domain (e.g., `slocumjunksolutions.com`) and click **Verify** $\rightarrow$ **Add domain**.
4. Click **Set up Netlify DNS** to generate 4 assigned nameservers:
   - `dns1.p01.nsone.net`
   - `dns2.p01.nsone.net`
   - `dns3.p01.nsone.net`
   - `dns4.p01.nsone.net`
5. Log into the domain registrar (e.g., Cloudflare, GoDaddy, Namecheap) and replace the default nameservers with Netlify's 4 nameservers.

### Secondary Method: External DNS Records (A / CNAME)

If managing DNS externally at the registrar:

| Record Type | Host / Name | Target / Value |
| :--- | :--- | :--- |
| **A** | `@` | `75.2.60.5` |
| **CNAME** | `www` | `[your-site-name].netlify.app` |

---

## 4. Continuous Integration (CI/CD) Workflow

Once linked, any future changes or fixes pushed to the `main` branch on GitHub will automatically trigger a Netlify build and update the live website within seconds.
