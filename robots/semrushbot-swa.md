---
name: SemrushBot-SWA
operator: Semrush
website: https://www.semrush.com
documentation: https://www.semrush.com/bot/
category: seo
robots_txt_token: SemrushBot-SWA
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SemrushBot-SWA
  identity: Semrush
last_checked: 2026-10-15
---

# SemrushBot-SWA

## Description

SemrushBot-SWA is a Semrush crawler. Semrush's bot page says it is used by "the SEO Writing Assistant tool to check if URL is accessible".

## Behavior

It checks whether a URL is accessible for the SEO Writing Assistant. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are
not documented for SemrushBot-SWA. The crawl-delay and caching rules on Semrush's page are given for
SemrushBot only.

## User agents

Not published. Semrush gives only the `robots.txt` token `SemrushBot-SWA`, and no full string was found
in other bot lists.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SemrushBot-SWA
Disallow: /
```

Semrush gives this record "To block SemrushBot from checking URLs on your site for SWA tool". The other Semrush tokens must be blocked separately: see
`semrushbot.md`.

## IP ranges and verification

None published for SemrushBot-SWA. Semrush's bot page documents no IP list or reverse DNS method for it.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SemrushBot-SWA` for the bare token and for a string in the
`Mozilla/5.0 (compatible; <token>; +http://www.semrush.com/bot.html)` form used by SemrushBot (the
real string is not published). `src/modules/identity.js` sets the identity `Semrush` when the
forward-confirmed hostname ends with `.semrush.com`, or when the address is in the inline range
`85.208.98.0/24`. Semrush documents neither for SemrushBot-SWA: the hostname suffix is not documented for
any Semrush crawler, and the only documented range, `85.208.98.128/25`, is for Site Audit.

## Misc

SemrushBot and the other Semrush crawlers are described in `semrushbot.md`.

## Sources

- https://www.semrush.com/bot/ (checked 2026-10-15)
