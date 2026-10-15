---
name: MJ12bot
operator: Majestic-12 Ltd
website: https://majestic.com
documentation: https://mj12bot.com/
category: seo
robots_txt_token: MJ12bot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: MJ12bot
  identity: Majestic
last_checked: 2026-10-15
---

# MJ12bot

## Description

MJ12bot is the crawler of Majestic, a UK company (Majestic-12 Ltd, Birmingham). It builds a web
graph of links, used by Majestic's backlink tools such as Site Explorer. Majestic says full-text
search is still at the research stage.

## Behavior

MJ12bot is a distributed crawler. Volunteers can run the crawler software on their own broadband
connections, so requests come from many networks worldwide. Majestic notes that several instances
may occasionally crawl the same site at once.

It supports `Crawl-delay`, up to 20 seconds. Higher values are treated as 20. No default crawl
rate is given. Majestic says the robot does not cache web content. JavaScript rendering and
`robots.txt` caching are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; MJ12bot/v2.0.7; http://mj12bot.com/)
```

The operator page lists only the `MJ12bot` token and older versions (v1.4.4 to v1.4.8), not the
full v2 string.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: MJ12bot
Disallow: /
```

Majestic documents these extensions: `Crawl-delay` (max 20 seconds), redirects within the same
site when fetching `robots.txt`, Yahoo-style wildcards, and a more specific `Allow` overriding
`Disallow`. A `403` on `robots.txt` is treated as a full disallow. If `robots.txt` cannot be
fetched, crawling is assumed to be allowed. A section for `MJ12bot` replaces the `*` section
rather than adding to it.

## IP ranges and verification

None published. Majestic does not document reverse DNS hostnames, an IP list or an ASN, and asks
site owners not to block it by IP. For verification, site owners can ask Majestic for a
pre-arranged ident string, sent in the user agent or in a `CRAWLER-IDENT` header.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `MJ12bot`. Hyperwatch sets the identity
`Majestic` when the verified hostname ends with `.mj12bot.com`. This hostname suffix is not
documented by Majestic. Hyperwatch also sets `Majestic` for requests with no other identity whose
header signature is `3d36aa5118581a33dd2704f3b0c22a0b`.

## Misc

Contact: bot@majestic12.co.uk.

## Sources

- https://mj12bot.com/ (checked 2026-10-15)
