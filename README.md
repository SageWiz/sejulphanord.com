# sejulphanord.com

Single-file portfolio (index.html) plus an images folder. No build step.

## 1. Put it on GitHub Pages
1. Create a new public repo under `sagewiz`, e.g. `sejulphanord.com`.
2. Upload everything in this folder (index.html, CNAME, README.md, images/) and your CV as `Sejul-Phanord-CV.docx` next to index.html.
3. Repo Settings > Pages > Source: Deploy from a branch, `main`, `/ (root)`.
4. Custom domain: `sejulphanord.com` (the CNAME file already sets this). Tick "Enforce HTTPS" once it's available.

## 2. Point the domain (Namecheap > Domain List > Manage > Advanced DNS)
Remove the default parking records, then add:

| Type  | Host | Value               |
|-------|------|---------------------|
| A     | @    | 185.199.108.153     |
| A     | @    | 185.199.109.153     |
| A     | @    | 185.199.110.153     |
| A     | @    | 185.199.111.153     |
| CNAME | www  | sagewiz.github.io.  |

## 3. contact@sejulphanord.com -> Gmail
Advanced DNS > Mail Settings > Email Forwarding, save.
Then Domain tab > Redirect Email > Add Forwarder: alias `contact`, forward to `sejulphanord@gmail.com`.
Send a test email to contact@sejulphanord.com to confirm it lands.

## 4. Turn on the contact form
1. Go to https://web3forms.com, enter `contact@sejulphanord.com`, and grab the access key from the email.
2. In index.html, search for `PASTE-YOUR-WEB3FORMS-ACCESS-KEY-HERE` and replace it with the key.
3. Send yourself a test message from the live site.
Free plan: 250 submissions a month. The key is meant to be public; your address never appears on the page.

## Before going live
- Add `Sejul-Phanord-CV.docx` (consider a web copy without your home address and phone).
- Double-check the Work tab copy for anything your employer wouldn't want public (dry dock photos, system names).
