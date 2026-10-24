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

## Secret scan

The Phase A §7.2 scan (no `.git`, `.env`, `.ftpconfig`, `.htpasswd`, `debug.log`, `*.php`, `*.sql*`; no `DB_PASSWORD`/`AUTH_KEY`/private keys/`phpinfo()`/`mysql_connect` in any text file) found nothing.

Source: the export tarball `src/www.winnipegelection.ca.tar.gz`, sha256 `a89d031f17231f9b4685ab239ce16f1f7936d71e08c4c4c8a441f5b31b2381b1`.
