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

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: dksearch-bot
Disallow: /
```

The token is the product name in the user agent. Whether the robot reads `robots.txt` is not
documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `dksearch-bot`. `src/modules/identity.js` has no rule for
it, so it gets no identity.

## Misc

- Version `0.1` in the user agent suggests an early or experimental crawler.
- Web searches for the name found no documentation, announcement or third-party profile.

## Sources

- https://example.dk/dksearch-bot (checked 2026-10-15, no response)
- https://www.ordbogen.com/ (checked 2026-10-15)
