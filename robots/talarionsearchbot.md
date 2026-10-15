---
name: TalarionSearchBot
operator: Talarion, Inc.
website: https://talarion.com
documentation: null
category: ai-search
robots_txt_token: TalarionSearchBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: TalarionSearchBot
  identity: null
last_checked: 2026-10-15
---

# TalarionSearchBot

## Description

TalarionSearchBot names Talarion in its user agent, through the contact address
`contact@talarion.tech`. The domain `talarion.tech` redirects to `talarion.com`, the site of
Talarion, Inc. Talarion sells a search API for AI models, aimed at information that models do not
already know, such as recent events. A third-party bot directory describes the robot as the
crawler that indexes recent web content for that search API. Talarion's own site does not mention
a crawler.

## Behavior

Not documented by the operator. No robot documentation page was found: `talarion.com/bot` and
`talarion.com/crawler` return 404. The user agent contains the word `research`, which is not
explained anywhere.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; TalarionSearchBot/1.0; research; contact: contact@talarion.tech)
```

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8`
- `accept-language`: `en-us,en-gb,en;q=0.7,*;q=0.3`
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: TalarionSearchBot
Disallow: /
```

The token is taken from the user agent. The operator does not state whether the robot obeys
`robots.txt`.

## IP ranges and verification

None published. No IP list, reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS396982 Google LLC: `136.108.120.0/24`, `35.231.141.0/24`, `34.73.170.0/24`, `136.108.160.0/24`

Reverse DNS hostnames:

- `*.bc.googleusercontent.com` (forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `TalarionSearchBot`. Hyperwatch has no
identity for it, since there is no way to verify it.

## Misc

Nothing else documented.

## Sources

- https://talarion.com/ (checked 2026-10-15)
- https://talarion.com/robots.txt (checked 2026-10-15)
- https://knownagents.com/agents/talarionsearchbot (checked 2026-10-15)
