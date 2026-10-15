---
name: Reflectionbot
operator: Reflection AI
website: https://reflection.ai
documentation: https://reflection.ai/legal/reflectionbot
category: ai-training
robots_txt_token: Reflectionbot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://reflection.ai/bot/ips.json
  hostnames: [".reflection.ai"]
hyperwatch:
  family: Reflectionbot
  identity: Reflection
last_checked: 2026-10-15
---

# Reflectionbot

## Description

Reflectionbot is the web crawler of Reflection AI, a company that builds open AI models. It visits
publicly available web pages to help build and improve Reflection AI's models. Reflection AI says
it is the only user agent it crawls with.

## Behavior

- `robots.txt`: read and honored. Changes are usually picked up within about a day.
- Reflection AI asks site owners to use `robots.txt` rather than HTTP errors such as 403 to limit
  the crawler.
- Crawl rate, `Crawl-delay` and JavaScript rendering: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Reflectionbot/1.0; +https://reflection.ai/bot) Chrome/151.0.0.0 Safari/537.36
```

This is also the example string documented by Reflection AI. The version numbers may change, and
Reflection AI recommends matching on the `Reflectionbot` token only.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Reflection by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8` (100%) |
| `accept-language` | `en-US,en;q=0.9` (100%) |
| `sec-fetch-dest` | `document` (100%) |
| `sec-fetch-mode` | `navigate` (100%) |
| `sec-fetch-site` | `none` (100%) |
| `sec-fetch-user` | `?1` (100%) |
| `upgrade-insecure-requests` | `1` (100%) |

## Blocking with robots.txt

```
User-agent: Reflectionbot
Disallow: /
```

No other tokens or opt-out rules are documented.

## IP ranges and verification

Two methods are documented:

- IP list: https://reflection.ai/bot/ips.json. It is a JSON object with `creationTime` and
  `prefixes`, an array of objects with an `ipv4Prefix` key. On 2026-10-15 it held 2 IPv4
  prefixes (creation time 2026-09-22).
- Reverse DNS: crawler addresses resolve to hostnames under `reflection.ai`. In a lookup on
  2026-10-15 they had the form `reflectionbot-<n>-<n>.reflection.ai`.

ASN: not documented.


## Hyperwatch

`@hyperwatch/useragent` returns the family `Reflectionbot`. `src/modules/identity.js` sets the
identity `Reflection` when the reverse DNS name ends with `.reflection.ai` and is confirmed by a
forward lookup. The IP list is not used.

## Misc

The URL in the user agent, https://reflection.ai/bot, redirects to
https://reflection.ai/legal/reflectionbot.

## Sources

- https://reflection.ai/legal/reflectionbot (checked 2026-10-15)
- https://reflection.ai/bot/ips.json (checked 2026-10-15)
