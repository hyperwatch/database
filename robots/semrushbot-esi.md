---
name: SemrushBot-ESI
operator: Semrush
website: https://www.semrush.com
documentation: https://www.semrush.com/bot/
category: seo
robots_txt_token: SemrushBot-ESI
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SemrushBot-ESI
  identity: Semrush
last_checked: 2026-10-15
---

# SemrushBot-ESI

## Description

SemrushBot-ESI is a Semrush crawler. Semrush's bot page says it is used by "the Semrush Enterprise Site Intelligence product, which analyzes on-page SEO, technical and usability issues".

## Behavior

It crawls sites audited with Semrush Enterprise Site Intelligence. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are
not documented for SemrushBot-ESI. The crawl-delay and caching rules on Semrush's page are given for
SemrushBot only.

## User agents

Not published. Semrush gives only the `robots.txt` token `SemrushBot-ESI`, and no full string was found
in other bot lists.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SemrushBot-ESI
Disallow: /
```

Semrush gives this record "To block SemrushBot-ESI from crawling your site for services provided by Semrush Enterprise Site Intelligence". The other Semrush tokens must be blocked separately: see
`semrushbot.md`.

## IP ranges and verification

None published for SemrushBot-ESI. Semrush's bot page documents no IP list or reverse DNS method for it.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SemrushBot-ESI` for the bare token and for a string in the
`Mozilla/5.0 (compatible; <token>; +http://www.semrush.com/bot.html)` form used by SemrushBot (the
real string is not published). `src/modules/identity.js` sets the identity `Semrush` when the
forward-confirmed hostname ends with `.semrush.com`, or when the address is in the inline range
`85.208.98.0/24`. Semrush documents neither for SemrushBot-ESI: the hostname suffix is not documented for
any Semrush crawler, and the only documented range, `85.208.98.128/25`, is for Site Audit.

## Misc

SemrushBot and the other Semrush crawlers are described in `semrushbot.md`.

## Sources

- https://www.semrush.com/bot/ (checked 2026-10-15)
