---
name: FlipboardProxy
operator: Flipboard
website: https://flipboard.com
documentation: https://about.flipboard.com/proxy-service/
category: other
robots_txt_token: FlipboardProxy
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: FlipboardProxy
  identity: Flipboard
last_checked: 2026-11-10
---

# FlipboardProxy

## Description

FlipboardProxy is the proxy service Flipboard uses to fetch, check and prepare parts of web pages
for display in the Flipboard app.

## Behavior

Flipboard says requests usually come as a cluster of closely spaced requests, in response to a user
asking Flipboard to scan a social media feed and build a processed feed of its items in real time.
Crawl rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Flipboard names the user agents `Flipboard` and `FlipboardProxy` but gives no full string.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-10, pages, verified as Flipboard by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (100%) |
| `accept-language` | `en-US,en;q=0.5` (100%) |

## Blocking with robots.txt

```
User-agent: FlipboardProxy
Disallow: /
```

Flipboard does not say whether the proxy reads `robots.txt`. The token above is the name it gives.

## IP ranges and verification

None published. Flipboard says its requests "currently all originate from the Amazon EC2 cluster",
without ranges, hostnames or an ASN.

## Hyperwatch

`@hyperwatch/useragent` returns the family `FlipboardProxy` for user agents carrying
`FlipboardProxy/<version>`. In Hyperwatch `main` (after 5.4.0), `src/modules/identity.js` sets the
identity `Flipboard` on the forward-confirmed hostname `*.proxy.flipboard.com`. The pattern is not
documented by Flipboard, which says its requests come from Amazon EC2.

## Misc

The page (published 2023-03-09) points to Flipboard's help center for questions.

## Sources

- https://about.flipboard.com/proxy-service/ (checked 2026-10-15)
