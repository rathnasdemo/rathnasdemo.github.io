# rathnasdemo.github.io: root site for Galascribe demo sites

This repository is the **root GitHub Pages site** of the `rathnasdemo` organisation. Galascribe builds a free preview site for a creator in this organisation (one repository per creator, for example `rathnasdemo/henry-stewart`). This root site does two jobs for all of them.

## 1. It gives every demo site its address

The custom domain `demo.galascribe.com` is set on this repository (the `CNAME` file and Settings → Pages). GitHub then serves every project site in the organisation that has no domain of its own under that domain:

| Repository | Served at |
|---|---|
| `rathnasdemo/<slug>` | `https://demo.galascribe.com/<slug>/` |
| `rathnasdemo/rathnasdemo.github.io` (this one) | `https://demo.galascribe.com/` |

The old `https://rathnasdemo.github.io/<slug>/` addresses redirect there. A repository that sets its own custom domain (for example `rathnasdemo/galascribe-blog` at `blog.galascribe.com`) keeps it.

DNS: `demo.galascribe.com` is a `CNAME` to `rathnasdemo.github.io` in Cloudflare, DNS only (not proxied), so GitHub issues and renews the HTTPS certificate.

## 2. It hides unclaimed demo sites from search engines

`robots.txt` here (`Disallow: /`) is served at the root of the domain, so it covers every demo site under `demo.galascribe.com/`. Demo sites are previews built from a creator's videos before the creator has claimed them, so they must not be indexed. When a creator claims a site, it moves to their own GitHub account and address, and this rule no longer applies to it.

## Files

| File | Purpose |
|---|---|
| `CNAME` | `demo.galascribe.com`, the domain for every demo site |
| `robots.txt` | `Disallow: /`, keeps all demo sites out of search engines |
| `index.html` | The page at `https://demo.galascribe.com/` (no index, links to galascribe.com) |
| `.nojekyll` | Serves the files as they are, without a Jekyll build |

## Before changing anything

- **Do not delete this repository or remove the custom domain.** Every demo site's links and its publishing depend on `demo.galascribe.com`.
- **Do not change `robots.txt`** unless demo sites should become searchable.
- Galascribe expects demo sites at this domain. Changing it needs a matching change in Galascribe and a re-publish of every demo site.
