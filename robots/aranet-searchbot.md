---
name: Aranet-SearchBot
operator: Unknown
website: https://aranet.ai
documentation: https://aranet.ai/bot
category: unknown
robots_txt_token: Aranet-SearchBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Aranet-SearchBot
  identity: Aranet
last_checked: 2026-10-15
---

# Aranet-SearchBot

## Description

Aranet-SearchBot points to `https://aranet.ai/bot` in its user agent. On 2026-10-15 the domain
`aranet.ai` had no address in DNS, so that page could not be fetched. No page from the operator
was found, so its operator and purpose are not confirmed. Known Agents describes it as an
undocumented AI agent.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Aranet-SearchBot/1.0; +https://aranet.ai/bot) Chrome/131.0.0.0 Safari/537.36
```

This string comes from Known Agents. The operator's page could not be fetched.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Aranet-SearchBot
Disallow: /
```

The token is taken from the user agent. Whether the robot obeys `robots.txt` is not documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `Aranet-SearchBot`. Hyperwatch sets the
identity `Aranet` when the reverse DNS name ends with `.googleusercontent.com`. This is a cloud
hostname: any Google Cloud customer passes it. The hostname is also not confirmed by a forward
lookup, so whoever controls an address's reverse DNS can set it. The operator documents no
hostname or range to check against.

## Misc

Nothing else documented.

## Sources

- https://aranet.ai/bot (checked 2026-10-15, the domain did not resolve)
- https://knownagents.com/agents/aranet-searchbot (checked 2026-10-15)
