---
name: Linespider
operator: LINE
website: https://line.me
documentation: https://help2.line.me/linesearchbot/web/?contentId=50006055&lang=en
category: search-engine
robots_txt_token: Linespider
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Linespider
  identity: Line
last_checked: 2026-10-15
---

# Linespider

## Description

Linespider is a web crawler managed by LINE. LINE says it provides search results for LINE
services.

## Behavior

LINE says Linespider follows the Robots Exclusion Protocol and only crawls pages within the limits
a site's `robots.txt` sets. Crawl rate, `Crawl-delay` support, JavaScript rendering and how often
`robots.txt` is re-read are not documented.

## User agents

Exact strings, one per line (`W.X.Y.Z` is a browser version):

```
Mozilla/5.0 (compatible; Linespider/1.1; +https://lin.ee/4dwXkTH)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Linespider/1.1; +https://lin.ee/4dwXkTH) Chrome/W.X.Y.Z Safari/537.36
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Linespider
Disallow: /
```

## IP ranges and verification

None published. LINE documents no IP list, reverse DNS hostnames or ASN.

## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `Linespider`. `src/modules/identity.js`
sets the identity `Line` when the unconfirmed hostname ends with `.search.line-apps.com`. LINE does
not document that suffix, and the check is not forward-confirmed.

## Misc

The link in the user agent, https://lin.ee/4dwXkTH, redirects to LINE's help page.

## Sources

- https://help2.line.me/linesearchbot/web/?contentId=50006055&lang=en (checked 2026-10-15)
