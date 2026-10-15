---
name: VivianCrawler
operator: unknown
website: https://vivian.d0a.net
documentation: null
category: search-engine
robots_txt_token: VivianCrawler
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: VivianCrawler
  identity: null
last_checked: 2026-10-15
---

# VivianCrawler

## Description

VivianCrawler describes itself in its user agent as a "search engine indexer" and links to
https://vivian.d0a.net. That site did not respond when checked (a Cloudflare error page), and no
other information about the operator or the search engine could be found.

## Behavior

Not documented.

## User agents

```
VivianCrawler/1.0 (https://vivian.d0a.net; search engine indexer)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: VivianCrawler
Disallow: /
```

The token is not documented, and it is not known whether the robot reads `robots.txt`.
`VivianCrawler` is the product name in the user agent.

## IP ranges and verification

None published.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS20055 Wholesail networks LLC (not a hosting network: prefixes not listed)

Reverse DNS hostnames:

- `*.bvtn.or.ptr.ziplyfiber.com` (not forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `VivianCrawler`. `src/modules/identity.js`
has no rule for it, so it gets no identity.

## Misc

`https://vivian.d0a.net` and `https://d0a.net` returned Cloudflare error 1033 (tunnel not
reachable) on 2026-10-15. A web search for the name found no page about it.

## Sources

- https://vivian.d0a.net (unreachable) (checked 2026-10-15)
- Web search for "VivianCrawler" and "vivian.d0a.net" (no relevant result) (checked 2026-10-15)
