---
name: DuckAssistBot
operator: DuckDuckGo
website: https://duckduckgo.com
documentation: https://duckduckgo.com/duckduckgo-help-pages/results/duckassistbot
category: ai-search
robots_txt_token: DuckAssistBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://duckduckgo.com/duckassistbot.json
  hostnames: []
hyperwatch:
  family: DuckAssistBot
  identity: DuckDuckGo
last_checked: 2026-11-12
---

# DuckAssistBot

## Description

DuckAssistBot is a DuckDuckGo crawler that fetches pages in real time for the AI-assisted answers
in DuckDuckGo Search. DuckDuckGo states: "This data is not used in any way to train AI models."

## Behavior

Pages are fetched in real time when building AI-assisted answers. Crawl rate, `Crawl-delay`
support, JavaScript rendering and `robots.txt` caching are not documented. A `robots.txt` change
takes effect after 72 hours. Opting out does not affect a site's ranking in DuckDuckGo results.

## User agents

Exact strings, one per line:

```
DuckAssistBot/1.1 (https://duckduckgo.com/duckassistbot)
DuckAssistBot/1.2; (+http://duckduckgo.com/duckassistbot.html)
```

The documented string is `DuckAssistBot/1.2; (+http://duckduckgo.com/duckassistbot.html)`.

## Observed HTTP headers

Based on dozens of requests seen on 2026-10-15, all paths (`robots.txt` and pages). Hyperwatch did not verify this robot then, so other clients using its name may be included.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (60%), `image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (30%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exch` (10%) |
| `accept-language` | `en-US,en;q=0.9` (40%) |
| `priority` | `i` (30%), `u=0, i` (10%) |
| `referer` | `(present)` (30%) |
| `sec-ch-ua` | `"Chromium";v="154", "Google Chrome";v="154", "Not A(Brand";v="99"` (40%) |
| `sec-ch-ua-mobile` | `?0` (40%) |
| `sec-ch-ua-platform` | `"Linux"` (40%) |
| `sec-fetch-dest` | `image` (30%), `document` (10%) |
| `sec-fetch-mode` | `no-cors` (30%), `navigate` (10%) |
| `sec-fetch-site` | `cross-site` (30%), `none` (10%) |
| `sec-fetch-storage-access` | `active` (30%) |
| `sec-fetch-user` | `?1` (10%) |
| `signature` | `(present)` (100%) |
| `signature-agent` | `"https://assistbot.duckduckgo.com"` (100%) |
| `signature-input` | `(present)` (100%) |
| `upgrade-insecure-requests` | `1` (10%) |

## Blocking with robots.txt

```
User-agent: DuckAssistBot
Disallow: /
```

Blocking DuckAssistBot does not block DuckDuckBot, and the reverse. Problems with the opt-out can
be reported to crawling@duckduckgo.com.

## IP ranges and verification

DuckDuckGo lists the source addresses on the help page and as JSON at
https://duckduckgo.com/duckassistbot.json. The format is an object with `creationTime` and a
`prefixes` array of `{"ipv4Prefix": ...}` objects. On the check date it held 486 IPv4 entries
(mostly single `/32` addresses), with `creationTime` 2026-09-01, and its content was identical to
https://duckduckgo.com/duckduckbot.json. No IPv6 entries, reverse DNS names or ASN are documented.

DuckAssistBot also signs its requests with Web Bot Auth (RFC 9421), with the `Signature-Agent`
value `"https://assistbot.duckduckgo.com"` (seen in the requests above; DuckDuckGo's pages checked
don't document it). The key directory,
https://assistbot.duckduckgo.com/.well-known/http-message-signatures-directory, held one `OKP` /
`Ed25519` key on 2026-11-12, whose `kid` is its JWK thumbprint, so a signature's `keyid` finds it
either way.


## Hyperwatch

`@hyperwatch/useragent` returns the family `DuckAssistBot`. In Hyperwatch 5.6.0,
`src/modules/identity.js` first sets the identity `DuckDuckGo` on a verified signature of
`https://bot.duckduckgo.com` (DuckDuckBot's), whatever the user agent ("signed only"). Then, for
the families `DuckDuckGo` (the DuckDuckGo browser's user agent), `DuckDuckBot`, `DuckDuckBot-Https`,
`DuckAssistBot` and `DuckDuckGo-Favicons-Bot`, it checks the forward-confirmed hostname
`*.crawl.duckduckgo.com`, a verified signature of `https://assistbot.duckduckgo.com`, then the
published lists (`duckduckbot-ips.json` and `duckassistbot-ips.json`, joined). Signatures need the
`webbotauth` module, off by default. DuckDuckGo documents no reverse DNS names: the hostname
pattern is Hyperwatch's own.

## Misc

- DuckDuckBot is DuckDuckGo's search crawler, documented at
  https://duckduckgo.com/duckduckgo-help-pages/results/duckduckbot with the user agent
  `DuckDuckBot/1.1; (+http://duckduckgo.com/duckduckbot.html)` and the address list
  https://duckduckgo.com/duckduckbot.json. It "respects WWW::RobotRules".
- `@hyperwatch/useragent` returns the family `DuckDuckBot` for that string. It shares this
  robot's rule (see "Hyperwatch" above and [DuckDuckBot](duckduckbot.md)).

## Sources

- https://duckduckgo.com/duckduckgo-help-pages/results/duckassistbot (checked 2026-10-15)
- https://duckduckgo.com/duckassistbot.json (checked 2026-10-15)
- https://duckduckgo.com/duckduckgo-help-pages/results/duckduckbot (checked 2026-10-15)
- https://duckduckgo.com/duckduckbot.json (checked 2026-10-15)
- https://assistbot.duckduckgo.com/.well-known/http-message-signatures-directory (checked 2026-11-12)
