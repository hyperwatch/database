---
name: VelenPublicWebCrawler
operator: Velen (for Hunter)
website: https://velen.io
documentation: https://velen.io/crawler
category: other
robots_txt_token: VelenPublicWebCrawler
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: VelenPublicWebCrawler
  identity: Velen
last_checked: 2026-10-15
---

# VelenPublicWebCrawler

## Description

Velen says its crawler is "written in Go for Hunter" and analyzes millions of public pages every
month. Its stated goal is "to build business datasets and machine learning models to better
understand the web". It only crawls publicly accessible pages, not pages behind a login or other
authentication.

## Behavior

Velen says the crawler follows `robots.txt` and meta instructions. It "usually" crawls no more than
one page at a time and one page every 2 seconds. Changes to `robots.txt` are picked up "within a
few hours". JavaScript rendering and `Crawl-delay` support are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; VelenPublicWebCrawler/1.0; +https://velen.io)
```

The operator page gives only the token `VelenPublicWebCrawler`. The full string comes from Known
Agents.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: VelenPublicWebCrawler
Disallow: /
```

## IP ranges and verification

None published. No hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `VelenPublicWebCrawler`. Hyperwatch sets
the identity `Velen` when the reverse DNS name ends with `.googleusercontent.com`. This is a cloud
hostname: any Google Cloud customer passes it. The hostname is also not confirmed by a forward
lookup. Velen does not document running on Google Cloud.

## Misc

Problems and feedback go to engineering@velen.io.

## Sources

- https://velen.io/crawler (checked 2026-10-15)
- https://knownagents.com/agents/velenpublicwebcrawler (checked 2026-10-15)
