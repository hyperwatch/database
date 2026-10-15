---
name: dksearch-bot
operator: Unknown
website: null
documentation: null
category: research
robots_txt_token: dksearch-bot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: dksearch-bot
  identity: null
last_checked: 2026-10-15
---

# dksearch-bot

## Description

dksearch-bot describes itself in its user agent as a "research crawler". No public page describes
it. The contact address in the user agent is at `ordbogen.com`, the domain of Ordbogen, a Danish
online dictionary company. Nothing else confirms that Ordbogen runs it or what it is for.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
dksearch-bot/0.1 (+https://example.dk/dksearch-bot; research crawler; contact: lbk@ordbogen.com)
```

The URL in the string points to `example.dk`, which looks like a placeholder. It could not be
loaded on the check date (no HTTP or HTTPS response).

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-10-15, all paths (`robots.txt` and pages). Hyperwatch does not verify this robot, so other clients using its name may be included.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (100%) |
| `accept-language` | `da, en;q=0.8` (100%) |
| `sec-fetch-mode` | `cors` (100%) |

## Blocking with robots.txt

```
User-agent: dksearch-bot
Disallow: /
```

The token is the product name in the user agent. Whether the robot reads `robots.txt` is not
documented.

## IP ranges and verification

None published.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS3356 Level 3 Parent, LLC: `205.188.212.0/24`, `205.188.213.0/24`

## Hyperwatch

`@hyperwatch/useragent` returns the family `dksearch-bot`. `src/modules/identity.js` has no rule for
it, so it gets no identity.

## Misc

- Version `0.1` in the user agent suggests an early or experimental crawler.
- Web searches for the name found no documentation, announcement or third-party profile.

## Sources

- https://example.dk/dksearch-bot (checked 2026-10-15, no response)
- https://www.ordbogen.com/ (checked 2026-10-15)
