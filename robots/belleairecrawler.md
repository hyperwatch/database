---
name: BelleaireCrawler
operator: Unknown
website: https://belleaire.xyz
documentation: null
category: unknown
robots_txt_token: BelleaireCrawler
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: BelleaireCrawler
  identity: null
last_checked: 2026-10-15
---

# BelleaireCrawler

## Description

BelleaireCrawler points to `https://belleaire.xyz/bot` in its user agent. That page returns 404.
The site `belleaire.xyz` is BelleAire, a small social site where people can post without an
account. Its pages do not mention a crawler. No other source describing this robot was found, so
its operator and purpose are not confirmed.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
BelleaireCrawler/1.0 (+https://belleaire.xyz/bot)
```

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: BelleaireCrawler
Disallow: /
```

The token is taken from the user agent. Whether the robot obeys `robots.txt` is not documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `BelleaireCrawler`. Hyperwatch has no
identity for it, since there is no way to verify it.

## Misc

Nothing else documented.

## Sources

- https://belleaire.xyz/bot (checked 2026-10-15, returns 404)
- https://belleaire.xyz/ (checked 2026-10-15)
- https://belleaire.xyz/robots.txt (checked 2026-10-15)
