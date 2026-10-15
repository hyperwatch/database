---
name: KeenableBot
operator: Keenable.ai, Inc.
website: https://keenable.ai
documentation: https://app.keenable.ai/bot
category: ai-search
robots_txt_token: KeenableBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://app.keenable.ai/bot/keenablebot.json
  hostnames: []
hyperwatch:
  family: KeenableBot
  identity: Keenable
last_checked: 2026-10-15
---

# KeenableBot

## Description

KeenableBot is the crawler of Keenable.ai, Inc. Keenable sells web search and content access APIs
for AI agents. KeenableBot collects public pages to build and maintain the Keenable search index.
That index answers queries from AI agents and applications, and the answers cite the source page
with a link.

## Behavior

Keenable says it follows the Robots Exclusion Protocol (RFC 9309). A group naming its token takes
precedence over a `User-agent: *` group. Rules take effect after its next fetch of `robots.txt`;
how often it fetches `robots.txt` is not documented.

It reads `noindex`, `nofollow` and `none` in `<meta name="robots">` tags and in the
`X-Robots-Tag` header. A directive addressed to `keenablebot` applies to it specifically.

Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented. Site owners can
ask for a lower crawl rate at abuse@keenable.ai.

## User agents

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; KeenableBot/1.0; +https://keenable.ai/bot)
```

This matches the string documented by Keenable.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: KeenableBot
Disallow: /
```

Keenable documents this to block both of its agents:

```
User-agent: KeenableBot
User-agent: Keenable-User
Disallow: /
```

Each token is controlled on its own. Disallowing KeenableBot removes the site from the Keenable
index and from answers built on it.

## IP ranges and verification

Keenable publishes one IP list per agent, in the same JSON format as Googlebot's
(`creationTime` and a `prefixes` array of `ipv4Prefix` objects):

- KeenableBot: https://app.keenable.ai/bot/keenablebot.json (30 IPv4 `/32` entries, no IPv6,
  `creationTime` 2026-10-09)
- Keenable-User: https://app.keenable.ai/bot/keenable-user.json (7 IPv4 `/32` entries, no IPv6)

Keenable states that a request naming one of its tokens from an address outside that token's list
is not from Keenable. The addresses are on Google Cloud, so reverse DNS
(`*.googleusercontent.com`) proves nothing.

Keenable says it is adding Web Bot Auth signatures (HTTP Message Signatures), with key directories
at `keenablebot.keenable.ai` and `keenable-user.keenable.ai`. As of the documentation date its
requests do not carry signatures yet, and it says to check the address instead. No ASN is
documented.

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `KeenableBot`. In `src/modules/identity.js`,
Hyperwatch sets identity `Keenable` when the address is in `src/data/keenablebot-ips.json`, a copy
of the published list refreshed by `node scripts/fetch-keenable-ips.js`.

## Misc

Keenable-User is Keenable's second agent. It makes requests on behalf of a person, or an agent
acting for one, for example when someone asks for a specific page. It does not crawl
automatically. Its user agent is:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Keenable-User/1.0; +https://keenable.ai/bot)
```

Hyperwatch parses it as family `Keenable-User` and sets identity `Keenable` when the address is in
`src/data/keenable-user-ips.json`.

The documentation was first published in September 2026. The IP lists were added in October 2026.
Contact: abuse@keenable.ai.

## Sources

- https://keenable.ai/bot (redirects to https://app.keenable.ai/bot) (checked 2026-10-15)
- https://app.keenable.ai/bot (checked 2026-10-15)
- https://app.keenable.ai/bot/keenablebot.json (checked 2026-10-15)
- https://app.keenable.ai/bot/keenable-user.json (checked 2026-10-15)
