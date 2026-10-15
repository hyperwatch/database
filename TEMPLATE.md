---
name: ExampleBot
operator: Example Inc.
website: https://example.com
documentation: https://example.com/bot
category: search-engine
robots_txt_token: ExampleBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://example.com/examplebot.json
  hostnames: []
hyperwatch:
  family: ExampleBot
  identity: Example
last_checked: 2026-10-15
---

# ExampleBot

## Description

Who runs it and what it is for, in a few sentences.

## Behavior

What the operator documents: what it fetches and why, crawl rate, whether it renders JavaScript,
whether it follows `Crawl-delay`, how often it reads `robots.txt`. Say when something isn't
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ExampleBot/1.0; +https://example.com/bot)
```

## Observed HTTP headers

Headers other than the user agent, as sent by the robot: `accept`, `accept-language`,
`accept-encoding`, `from`, client hints, `sec-fetch-*`. Only what was observed, with how many
requests it is based on.

## Blocking with robots.txt

```
User-agent: ExampleBot
Disallow: /
```

Other tokens it obeys (or doesn't), special rules (`Crawl-delay`, opt-out tokens such as
`Google-Extended`), and anything the operator says it ignores.

## IP ranges and verification

How to tell the real robot from an impersonator: published IP list (URL and format), reverse DNS
hostnames, ASN. "None published" when there is nothing.

## Hyperwatch

How `@hyperwatch/useragent` parses it (agent family) and whether Hyperwatch verifies it as an
identity (`src/modules/identity.js`), and how.

## Misc

Anything else worth knowing: related robots from the same operator, history, controversies.

## Sources

- https://example.com/bot (checked 2026-10-15)
