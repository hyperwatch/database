---
name: trendictionbot
operator: Trendiction S.A. (Luxembourg)
website: https://www.trendiction.com
documentation: http://www.trendiction.de/bot
category: marketing
robots_txt_token: trendictionbot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: trendiction search
  identity: null
last_checked: 2026-11-10
---

# trendictionbot

## Description

trendictionbot is the crawler of Trendiction S.A., in Luxembourg. It crawls public websites,
including news sites, message boards and blogs with their comments, for Trendiction's public
search engine and for clients who receive the data through its APIs: market research companies,
marketing agencies, search engines and other web applications.

## Behavior

Trendiction says it caches, uses gzip compression and `If-Modified-Since` / `ETag` to skip
unchanged pages, and adapts the crawl rate to the hits found, the rank of the site and its caches.
No number is given. `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64; trendictionbot0.5.0; trendiction search; http://www.trendiction.de/bot; please let us know of any problems; web at trendiction.com) Gecko/20100101 Firefox/125.0
```

The string starts like a desktop Firefox; the token `trendictionbot` is inside it.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-10, pages, from one of the networks listed below.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (100%) |
| `accept-charset` | `ISO-8859-1,utf-8;q=0.7,*;q=0.7` (100%) |
| `accept-language` | `en-gb,en;q=0.5` (100%) |
| `cache-control` | `max-age=0` (100%) |
| `pragma` | `no-cache` (100%) |
| `refresh-cache` | `1` (100%) |

## Blocking with robots.txt

```
User-Agent: trendictionbot
Disallow: /
```

Trendiction says a change to `robots.txt` can take up to 5 days to apply, because of its caching.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-11-07 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS24940 Hetzner Online GmbH: `144.76.22.0/24`, `144.76.23.0/24`, `144.76.14.0/24`, `116.202.33.0/24`

## Hyperwatch

`@hyperwatch/useragent` returns the family `trendiction search`. `src/modules/identity.js` has no
rule for it, so Hyperwatch sets no identity.

## Misc

Contact: web at trendiction.com, as the user agent says; Trendiction S.A., 12-16 avenue Monterey,
L-2163 Luxembourg.

## Sources

- http://www.trendiction.de/bot (checked 2026-11-10)
