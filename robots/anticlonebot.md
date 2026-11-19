---
name: AntiCloneBot
operator: AntiClone
website: https://anticlone.de
documentation: https://anticlone.de/bot
category: other
robots_txt_token: AntiCloneBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: AntiCloneBot
  identity: AntiClone
last_checked: 2026-11-19
---

# AntiCloneBot

## Description

AntiCloneBot is the crawler of AntiClone. It "finds copies of online shops (fake shops that copy a
real store's products, texts and images) for the owners of the copied shops".

## Behavior

AntiClone says the crawler usually looks at a website only once and reads few public pages:
`robots.txt`, the homepage and, for Shopify stores, a small sample of the product list. For other
shops it reads the product list or sitemap, only from the shop's own website, with a few product
images for a visual comparison. Pages that probably copy a shop are checked more closely and looked
at again later to see whether they are still online.

It honors `robots.txt` including `Crawl-delay`, and slows down when a website answers 429 or 430.
It does no logins, forms, orders or vulnerability tests, and follows no links or sitemaps to other
websites. For a possible copy, a browser records the page as evidence, "also as AntiCloneBot and
only if robots.txt allows it", loading the homepage once more like an ordinary visitor.

Crawl rate, JavaScript rendering by the crawler itself and how long `robots.txt` is cached are not
documented.

## User agents

Not documented as a full string: AntiClone's page gives the user agent as `AntiCloneBot` only.

```
AntiCloneBot
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: AntiCloneBot
Disallow: /
```

AntiClone says the block applies to the bot, and that a page reported by a merchant as a possible
copy is still looked at in person in a normal browser. `Crawl-delay` is honored. No other token is
documented.

## IP ranges and verification

None published. AntiClone says the crawler does not change IP addresses or use proxies to get
around a block, but lists no addresses, hostnames or ASN.

AntiClone says the crawler's requests are signed with Web Bot Auth, and that it is a verified bot
at Cloudflare. The `Signature-Agent` value is not documented; the key directory is
https://anticlone.de/.well-known/http-message-signatures-directory: on 2026-11-19 it held one
`OKP` / `Ed25519` key, with a `kid` equal to the key's JWK thumbprint, so the `keyid` is both. The
directory's own response was signed with that key.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 parses the documented value `AntiCloneBot` as family `AntiCloneBot`.
Since Hyperwatch 5.7.0, `src/modules/identity.js` sets the identity `AntiClone` signed only: a
verified signature of `https://anticlone.de` (the `signedOnly` map, checked before the rules per
family) gives `AntiClone` whatever the user agent. `https://anticlone.de` is in
`src/data/webbotauth-agents.json` (robot `AntiCloneBot`), and its one key is in
`webbotauth-keys.json`, the same as the published directory on 2026-11-19. There is no rule for the
family: without the `webbotauth` module (off by default) or without a valid signature, the request
gets no identity. This matches AntiClone's documentation, which publishes no addresses or
hostnames.

## Misc

- Contact: the contact form on anticlone.de (no address given on the crawler page).
- AntiClone says it keeps domain, shop system, page title, public shop IDs, image file names and
  fingerprints of texts and product images, product titles and shop contacts only as keyed hashes,
  nothing about visitors, in the European Union, and deletes a website's entries on request.

## Sources

- https://anticlone.de/bot (checked 2026-11-19)
- https://anticlone.de/.well-known/http-message-signatures-directory (checked 2026-11-19)
