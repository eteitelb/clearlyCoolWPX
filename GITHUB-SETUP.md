# Hosting on GitHub Pages + Pointing Your Wix Domain

## 1. Put the site on GitHub

1. Create a free account at github.com if you don't have one.
2. Click **New repository**. Name it anything (e.g. `clearly-cool-site`). Set it to **Public**.
3. Upload the contents of this `clearly-cool-site/` folder (index.html, photos/, etc.).
4. Go to **Settings → Pages**.
5. Under "Branch", select `main` and click **Save**.

GitHub will give you a URL like `https://yourusername.github.io/clearly-cool-site/` within ~1 minute.

---

## 2. Point your Wix domain (clearly-cool.com) at GitHub Pages

Yes — this is straightforward. Wix lets you manage DNS even for domains you bought through them.

### Step-by-step

1. Log into **Wix** → **Domains** → click **clearly-cool.com** → **Manage** → **Advanced** → **DNS Records**.

2. **Delete** any existing A records pointing to Wix servers.

3. Add **four A records** pointing to GitHub Pages:

   | Type | Host | Value            |
   |------|------|-----------------|
   | A    | @    | 185.199.108.153 |
   | A    | @    | 185.199.109.153 |
   | A    | @    | 185.199.110.153 |
   | A    | @    | 185.199.111.153 |

4. Add a **CNAME record** for `www`:

   | Type  | Host | Value                        |
   |-------|------|------------------------------|
   | CNAME | www  | yourusername.github.io       |

5. Back in GitHub → **Settings → Pages → Custom domain**, enter `clearly-cool.com` and click **Save**. Check "Enforce HTTPS".

6. Create a file called `CNAME` (no extension) in the root of your repo containing just:
   ```
   clearly-cool.com
   ```

DNS changes propagate in 15 minutes to a few hours. After that, `clearly-cool.com` will load your GitHub-hosted site with HTTPS.

---

## 3. Adding your own photos

Drop photos into the `photos/` folder in this repo. Then update the `src` attributes in `index.html` — each image has a comment showing the suggested filename, e.g.:

```html
<!-- Replace with photos/farrowing.jpg once added -->
<img src="photos/farrowing.jpg" ... />
```

Suggested filenames:
- `photos/farrowing.jpg` — sow under panel in farrowing crate
- `photos/gestation.jpg` — gestation barn cooling station
- `photos/product.jpg` — panel close-up
- `photos/panel-install.jpg` — install shot for "How It Works"
