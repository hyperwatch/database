---
name: DuckDuckBot
operator: DuckDuckGo
website: https://duckduckgo.com
documentation: https://duckduckgo.com/duckduckgo-help-pages/results/duckduckbot
category: search-engine
robots_txt_token: DuckDuckBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://duckduckgo.com/duckduckbot.json
  hostnames: []
hyperwatch:
  family: DuckDuckBot
  identity: DuckDuckGo
last_checked: 2026-10-15
---

# DuckDuckBot

## Description

DuckDuckBot is DuckDuckGo's web crawler. DuckDuckGo says its job "is to constantly improve our
search results".

## Behavior

DuckDuckGo says it "respects WWW::RobotRules". Crawl rate, `Crawl-delay` support, JavaScript
rendering and `robots.txt` caching are not documented.

## User agents

Exact strings, one per line:

```
DuckDuckBot/1.1; (+http://duckduckgo.com/duckduckbot.html)
```

Hyperwatch's identity rule also names `DuckDuckBot-Https` and `DuckDuckGo-Favicons-Bot`.
DuckDuckGo does not document user agents with these names: its page on favicons
(https://duckduckgo.com/duckduckgo-help-pages/privacy/favicons) says favicons are fetched by its
own servers, without naming a robot.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: DuckDuckBot
Disallow: /
```

The page gives no `robots.txt` example; the token above is the robot's name. Blocking DuckDuckBot
does not block DuckAssistBot, and the reverse (see [DuckAssistBot](duckassistbot.md)).

## IP ranges and verification

DuckDuckGo lists the source addresses on the help page and as JSON at
https://duckduckgo.com/duckduckbot.json, an object with `creationTime` and a `prefixes` array of
`{"ipv4Prefix": ...}` objects. On 2026-10-15 it held 486 IPv4 entries and was dated 2026-09-01. Its
content was identical to https://duckduckgo.com/duckassistbot.json. No IPv6 addresses, reverse DNS
names or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `DuckDuckBot`. In Hyperwatch `main` (after 5.3.3),
`src/modules/identity.js` sets the identity `DuckDuckGo` for the families `DuckDuckGo` (the
DuckDuckGo browser's user agent), `DuckDuckBot`, `DuckDuckBot-Https`, `DuckAssistBot` and
`DuckDuckGo-Favicons-Bot` on an unconfirmed hostname ending with `.duckduckgo.com` or the published
lists (`duckduckbot-ips.json` and `duckassistbot-ips.json`, joined). DuckDuckGo documents no reverse
DNS names: the hostname suffix is Hyperwatch's own, and whoever controls an address's reverse DNS
can pass it.

## Misc

DuckAssistBot is DuckDuckGo's real-time fetcher for AI-assisted answers, with its own token and
the same address list.

## Sources

- https://duckduckgo.com/duckduckgo-help-pages/results/duckduckbot (checked 2026-10-15)
- https://duckduckgo.com/duckduckbot.json (checked 2026-10-15)
- https://duckduckgo.com/duckassistbot.json (checked 2026-10-15)
- https://duckduckgo.com/duckduckgo-help-pages/privacy/favicons (checked 2026-10-15)
