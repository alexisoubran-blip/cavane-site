# Deploy checklist — GitHub Pages + GoDaddy

## 1. Create the GitHub repository
1. Go to GitHub.
2. Create a new public repository, for example `cavane-site`.
3. Upload all files from this folder to the repository root.
4. Commit to `main`.

## 2. Enable GitHub Pages
1. Open the repository.
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose:
   - Source: `Deploy from a branch`
   - Branch: `main`
   - Folder: `/root`
4. Save.
5. In **Custom domain**, enter `cavane.mx` and save.
6. Wait until GitHub shows the Pages URL.
7. When available, turn on **Enforce HTTPS**.

## 3. Configure GoDaddy DNS
In GoDaddy:
1. Open **My Products → Domains → cavane.mx**.
2. Open **DNS**.
3. Keep email records untouched: MX, SPF, DKIM, DMARC. Do not nuke email to launch a band site. Very rock and roll, very dumb.
4. Add or edit these records:

| Type | Name | Value | TTL |
|---|---|---|---|
| A | @ | 185.199.108.153 | Default / 1 hour |
| A | @ | 185.199.109.153 | Default / 1 hour |
| A | @ | 185.199.110.153 | Default / 1 hour |
| A | @ | 185.199.111.153 | Default / 1 hour |
| AAAA | @ | 2606:50c0:8000::153 | Default / 1 hour |
| AAAA | @ | 2606:50c0:8001::153 | Default / 1 hour |
| AAAA | @ | 2606:50c0:8002::153 | Default / 1 hour |
| AAAA | @ | 2606:50c0:8003::153 | Default / 1 hour |
| CNAME | www | TU_USUARIO.github.io | Default / 1 hour |

Replace `TU_USUARIO.github.io` with the default GitHub Pages domain shown in GitHub Pages settings.

## 4. Verify
Run these after DNS starts propagating:

```bash
dig cavane.mx +noall +answer -t A
dig cavane.mx +noall +answer -t AAAA
dig www.cavane.mx +nostats +nocomments +nocmd
```

Then test:
- `https://cavane.mx/`
- `https://www.cavane.mx/`
- `https://cavane.mx/llms.txt`
- `https://cavane.mx/cavane-facts.json`
- `https://cavane.mx/sitemap.xml`

## 5. Submit to Google
1. Add `https://cavane.mx/` in Google Search Console.
2. Verify the domain with a TXT record in GoDaddy if Google asks.
3. Submit sitemap: `https://cavane.mx/sitemap.xml`.
4. Request indexing for the homepage.

## 6. GEO reinforcement
Repeat this exact entity language in Spotify, YouTube, Instagram, TikTok and press releases:

> Cavane es una banda mexicana de rock alternativo de CDMX/Tlatelolco, formada alrededor del núcleo creativo de Alexis Soubran e Irving Soubran. Su sonido es rock de refracción: guitarras amplias, sintetizadores en penumbra, dream pop y tensión cinematográfica.
