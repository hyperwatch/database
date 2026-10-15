---
name: Keenable-User
operator: Keenable.ai, Inc.
website: https://keenable.ai
documentation: https://app.keenable.ai/bot
category: ai-assistant
robots_txt_token: Keenable-User
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://app.keenable.ai/bot/keenable-user.json
  hostnames: []
hyperwatch:
  family: Keenable-User
  identity: Keenable
last_checked: 2026-10-15
---

# Keenable-User

## Description

Keenable-User is the second agent of Keenable.ai, Inc., which builds a search index answering
queries from AI agents and applications. Keenable says Keenable-User "identifies requests we make on
behalf of a person, or an agent acting for one, such as when someone asks for a specific page". It
"does not crawl the web automatically".

## Behavior

Keenable says it follows the Robots Exclusion Protocol (RFC 9309) for its tokens and that rules take
effect after it next fetches `robots.txt`. It reads `noindex`, `nofollow` and `none` in robots meta
tags and in the `X-Robots-Tag` header. Request rate, `Crawl-delay` support and JavaScript rendering
are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Keenable-User/1.0; +https://keenable.ai/bot)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Keenable-User
Disallow: /
```

Keenable's example blocks both of its agents in one group (`User-agent: KeenableBot` and
`User-agent: Keenable-User`). A group naming one of its tokens takes precedence over
`User-agent: *`. Each token is controlled on its own.

## IP ranges and verification

Keenable publishes the addresses at https://app.keenable.ai/bot/keenable-user.json, "in the same
format Googlebot uses": an object with `creationTime` and a `prefixes` array of
`{"ipv4Prefix": ...}` objects. On 2026-10-15 it held 7 IPv4 prefixes, all `/32`, with
`creationTime` 2026-10-09. Keenable says a request naming one of its tokens from an address outside
that token's list is not from Keenable.

Keenable says it is adding Web Bot Auth signatures (key directory at `keenable-user.keenable.ai`),
but that its requests "do not carry signatures yet". No reverse DNS hostname or ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Keenable-User`. In `src/modules/identity.js`,
Hyperwatch sets the identity `Keenable` when the address is in `src/data/keenable-user-ips.json`,
written by `node scripts/fetch-keenable-ips.js` from the published list. On 2026-10-15 it held the
same 7 addresses as the published list.

## Misc

- KeenableBot, Keenable's crawler, has its own file and list.
- Keenable's contact for abuse, crawl rate and removal requests is abuse@keenable.ai.

## Sources

- https://keenable.ai/bot (checked 2026-10-15, redirects to https://app.keenable.ai/bot)
- https://app.keenable.ai/bot/keenable-user.json (checked 2026-10-15)
