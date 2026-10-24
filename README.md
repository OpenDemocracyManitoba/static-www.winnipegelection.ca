# www.winnipegelection.ca (static archive)

Static copy of **www.winnipegelection.ca**, taken from olddroplet (`odm-nginx-ruby-php-2018`, 159.203.24.194) on 2026-10-24, before the server was retired. Static landing page for winnipegelection.ca.

`site/` is the served web root as it was on disk (73 files), minus the files listed below. No crawl was needed: this site was already static.

## Serving

Serve `site/` as static files from the domain root.

## Left out of `site/`

* `.git/`
* `README.md`
* `contact.php`
* `contact2.php`
* `db.php`
* `docs/`
* `index.php.old`

These were left out because they were not site content: version control, PHP, or (per the archive plan) files that should not be public. The full web root is kept in a private archive repo.

## Links to internal or old hosts

None found (`upcoming.manitobaelection.ca`, `http://www.manitobaelection.ca`, `159.203.24.194`).

## Analytics removed

Google Tag Manager / Google Analytics (and the Google Ads tag that rides on `gtag.js`) were removed in Phase B of the olddroplet migration (owner decision D7, 2026-10-24) by `python3 -I strip_analytics.py www.winnipegelection.ca --apply`. Files changed: 1 HTML file. IDs: `AW-798203154`, `UA-17537013-1`. Each loader went together with its inline block and the comment around it. Other third-party scripts (fonts, embeds, Jetpack stats) were left as they were.

Snippet shapes removed (IDs and whitespace normalised):

* 1 ×

  ```html
  <script async src="https://www.googletagmanager.com/gtag/js?id=<ID>" ></script> <script> window.dataLayer = window.dataLayer || []; function gtag() { dataLayer.push(arguments); } gtag("js", new Date()); gtag("config", "<ID>"); gtag("config", "<ID>"); </script>
  ```

## Hosting

Served from **Cloudflare Workers static assets** (Phase B of the olddroplet migration). `wrangler.jsonc`, `.gitignore`, `site/404.html` and this section are written by `hosting.py` (`python3 -I hosting.py www.winnipegelection.ca <preview|routed|final>`).

* **Worker:** `static-www-winnipegelection-ca`, account `Stungeye@gmail.com's Account`.
* **Deploy:** `npx wrangler@4.148.0 deploy` from the repo root. Only `site/` is uploaded.
* **Routes:** `www.winnipegelection.ca/*` on zone `winnipegelection.ca`, over the existing proxied DNS record.
* **workers.dev:** https://static-www-winnipegelection-ca.stungeye.workers.dev. Per-version preview URLs are off (`preview_urls: false`).
* **Serving:** `html_handling: auto-trailing-slash` (`/foo` serves `foo.html`, `/foo/` serves `foo/index.html`; the other forms 307 to those) and `not_found_handling: 404-page` (`site/404.html`, a minimal page added in Phase B).
* **http → https:** the zone setting "Always Use HTTPS" (301 at Cloudflare's edge).
* **Redirect rules:** the `winnipegelection.ca` zone has a Single Redirect rule: `http.host eq "winnipegelection.ca"` → `concat("https://www.winnipegelection.ca", http.request.uri.path)`, query string kept, 301.
* **Rollback:** while the old origin is up, remove `routes` from `wrangler.jsonc` and deploy (or delete the route in the dashboard); the origin serves again at once. A bad version can be rolled back with `npx wrangler@4.148.0 rollback`.

## Secret scan

The Phase A §7.2 scan (no `.git`, `.env`, `.ftpconfig`, `.htpasswd`, `debug.log`, `*.php`, `*.sql*`; no `DB_PASSWORD`/`AUTH_KEY`/private keys/`phpinfo()`/`mysql_connect` in any text file) found nothing.

Source: the export tarball `src/www.winnipegelection.ca.tar.gz`, sha256 `a89d031f17231f9b4685ab239ce16f1f7936d71e08c4c4c8a441f5b31b2381b1`.
