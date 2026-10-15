---
name: SofyaBot
operator: Sofya
website: https://sofya.co
documentation: https://sofya.co/bot
category: ai-search
robots_txt_token: SofyaBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://sofya.co/bot/ips.json
  hostnames:
    - .sofya.co
hyperwatch:
  family: SofyaBot
  identity: Sofya
last_checked: 2026-10-15
---

# SofyaBot

## Description

SofyaBot is the web crawler of Sofya. It builds Sofya's own search index, served at
`search.sofya.co`. Sofya sells an API for AI agents and developers to search the web, fetch pages
as markdown, ask questions about a page and run multi-source research. Sofya says it builds an
independent index rather than reselling another engine's results.

## Behavior

Sofya says SofyaBot reads `robots.txt` and obeys it. Rules for `SofyaBot` take precedence,
otherwise it follows the rules for `*`. It honours `Crawl-delay`. Crawl rate, JavaScript rendering
and how often `robots.txt` is re-read are not documented. Which user agent Sofya's fetch API uses
is not documented.

## User agents

Exact strings, one per line:

```
SofyaBot/1.0 (+https://sofya.co/bot)
```

Sofya says this user agent is sent on every request.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SofyaBot
Disallow: /
```

To slow it down instead (one request every ten seconds):

```
User-agent: SofyaBot
Crawl-delay: 10
```

## IP ranges and verification

Sofya lists its crawling addresses on its bot page, each with a name such as `crawl-1.sofya.co`,
and says each named address has forward-confirmed reverse DNS.

The same list is published at https://sofya.co/bot/ips.json. The file is JSON with a
`creationTime` field and a `prefixes` array of objects with an `ipv4Prefix` key. On 2026-10-15 it
held 4 IPv4 prefixes, all `/32`, and was dated 2026-09-11. No IPv6 prefix and no ASN are
documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `SofyaBot`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `Sofya` on an unconfirmed hostname ending with
`.sofya.co` or the published list (`sofyabot-ips.json`). Sofya documents forward-confirmed reverse
DNS; the hostname is still not confirmed: whoever controls an address's reverse DNS can pass it.

## Misc

Problems and removal requests go to bot@sofya.co. Sofya says a report from a site owner takes
priority over anything else it is doing.

## Sources

- https://sofya.co/bot (checked 2026-10-15)
- https://sofya.co/bot/ips.json (checked 2026-10-15)
- https://sofya.co/ (checked 2026-10-15)
