# Future Reference: Switching to a Custom Domain

This document outlines the steps required to transition the Okanagan Rovercraft website from `joshchomps.github.io/ORC_Website/` to a custom domain (e.g., `okanaganrovercraft.ca`).

## 🛠️ Code Changes

When you are ready to move to a custom domain, you only need to update **one** file thanks to our use of dynamic links.

### 1. Update `astro.config.mjs`
Modify the `site` and `base` properties:

```javascript
import { defineConfig } from 'astro/config';

export default defineConfig({
  // 1. Change this to your new domain
  site: 'https://okanaganrovercraft.ca', 
  // 2. Change this back to the root
  base: '/', 
});
```

Because we used `import.meta.env.BASE_URL` for all our internal links, they will automatically update to point to the root of your new domain!

---

## 🌐 GitHub & DNS Setup

### 2. Update Repo Settings
1.  Go to your repository on GitHub.
2.  Navigate to **Settings** > **Pages**.
3.  In the **Custom domain** section, type your domain (e.g., `okanaganrovercraft.ca`) and click **Save**.

### 3. Configure DNS
You will need to log into your domain registrar (e.g., Namecheap, GoDaddy, Google Domains) and add the following:

- **CNAME Record**:
  - Name: `www`
  - Value: `joshchomps.github.io`
- **A Records** (For the apex domain):
  - Point your apex domain to GitHub's IP addresses:
    - `185.199.108.153`
    - `185.199.109.153`
    - `185.199.110.153`
    - `185.199.111.153`

### 4. Enforce HTTPS
Once the DNS has propagated, go back to the GitHub Pages settings and check the **Enforce HTTPS** box.

---

> [!TIP]
> Keep this file in your repository for future reference! 
