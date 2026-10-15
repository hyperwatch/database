---
name: SEOkicks
operator: Jobkicks SLU (SEOkicks)
website: https://www.seokicks.de
documentation: https://www.seokicks.de/robot.html
category: seo
robots_txt_token: SEOkicks
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SEOkicks
  identity: SEOkicks
last_checked: 2026-10-15
---

# SEOkicks

## Description

SEOkicks is the web crawler of SEOkicks.de, a backlink database run by Jobkicks SLU. It records
links from pages to other domains, with their anchor text and attributes, so that site owners can
look up which sites link to a given site.

## Behavior

SEOkicks says its crawlers wait at least one second between two page requests, and wait longer
when the server answers slowly. They only make `GET` requests, never `POST`. They obey common
`robots.txt` rules: blocking single files, directories or the whole domain.

`Crawl-delay`, JavaScript rendering and how often `robots.txt` is read are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SEOkicks; +https://www.seokicks.de/robot.html)
```

The page gives this string inside an example log line, and says the crawlers identify themselves
with the user agent `SEOkicks`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SEOkicks
Disallow: /
```

The page gives no `robots.txt` example and no token: `SEOkicks` is the name it uses for the user
agent.

## IP ranges and verification

None published. The page documents no IP list, reverse DNS name or ASN.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `SEOkicks`. Hyperwatch sets the identity
`SEOkicks` when the forward-confirmed hostname ends with `.seokicks.de`. The rule cites the robot
page, but that page does not document a hostname: the suffix is not from the operator.

## Misc

The page is in German; the English address https://en.seokicks.de/robot.html serves the same
German text. Problems can be reported to the address given on the page.

## Sources

- https://www.seokicks.de/robot.html (checked 2026-10-15)
- https://en.seokicks.de/robot.html (checked 2026-10-15)
