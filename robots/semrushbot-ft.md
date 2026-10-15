---
name: SemrushBot-FT
operator: Semrush
website: https://www.semrush.com
documentation: https://www.semrush.com/bot/
category: seo
robots_txt_token: SemrushBot-FT
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SemrushBot-FT
  identity: Semrush
last_checked: 2026-10-15
---

# SemrushBot-FT

## Description

SemrushBot-FT is a Semrush crawler. Semrush's bot page says it is used by "the Plagiarism Checker tool, to verify whether the content being checked appears on your website".

## Behavior

It fetches pages to check whether content submitted to the Plagiarism Checker appears on a site. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are
not documented for SemrushBot-FT. The crawl-delay and caching rules on Semrush's page are given for
SemrushBot only.

## User agents

Not published. Semrush gives only the `robots.txt` token `SemrushBot-FT`, and no full string was found
in other bot lists.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SemrushBot-FT
Disallow: /
```

Semrush gives this record "To block SemrushBot-FT from crawling your site for Plagiarism Checker and similar tools". The other Semrush tokens must be blocked separately: see
`semrushbot.md`.

## IP ranges and verification

None published for SemrushBot-FT. Semrush's bot page documents no IP list or reverse DNS method for it.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SemrushBot-FT` for the bare token and for a string in the
`Mozilla/5.0 (compatible; <token>; +http://www.semrush.com/bot.html)` form used by SemrushBot (the
real string is not published). `src/modules/identity.js` sets the identity `Semrush` when the
forward-confirmed hostname ends with `.semrush.com`, or when the address is in the inline range
`85.208.98.0/24`. Semrush documents neither for SemrushBot-FT: the hostname suffix is not documented for
any Semrush crawler, and the only documented range, `85.208.98.128/25`, is for Site Audit.

## Misc

SemrushBot and the other Semrush crawlers are described in `semrushbot.md`.

## Sources

- https://www.semrush.com/bot/ (checked 2026-10-15)
