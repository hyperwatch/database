---
name: image-crawler
operator: Unknown
website: null
documentation: null
category: unknown
robots_txt_token: image-crawler
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: image-crawler
  identity: null
last_checked: 2026-10-15
---

# image-crawler

## Description

The user agent `image-crawler/0.1` has no URL, contact address or operator name. No public source
describing it was found. Its operator and purpose are unknown. The name is generic and may be used
by unrelated tools.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
image-crawler/0.1
```

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8`
- `accept-language`: `en`
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: image-crawler
Disallow: /
```

The token is taken from the user agent. Whether the robot reads `robots.txt` is unknown.

## IP ranges and verification

None published.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS24940 Hetzner Online GmbH: `95.216.75.0/24`, `65.108.38.0/24`

Reverse DNS hostnames:

- `*.clients.your-server.de` (forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `image-crawler`. Hyperwatch has no
identity for it, since there is no way to verify it.

## Misc

Nothing known.

## Sources

- No operator page found. Web search for the exact string returned no relevant result (checked 2026-10-15).
