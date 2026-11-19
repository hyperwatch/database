---
name: HyperSearchBot
operator: EcoGPT
website: https://ecogpt.com
documentation: https://hypersearchbot.ecogpt.com/
category: ai-search
robots_txt_token: HyperSearchBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://hypersearchbot.ecogpt.com/hypersearchbot.json
  hostnames: []
hyperwatch:
  family: HyperSearchBot
  identity: EcoGPT
last_checked: 2026-11-19
---

# HyperSearchBot

## Description

HyperSearchBot is the web crawler of EcoGPT, an AI chat assistant. EcoGPT says it "fetches public
pages to build EcoGPT's search index, so EcoGPT can show its readers links to your site", and that
"its crawl is for search only".

## Behavior

From EcoGPT's page:

- It reads `robots.txt` before any other page of a site, following RFC 9309.
- It sends one request at a time per site, at least 5 seconds apart.
- It honours `Crawl-delay` up to 30 seconds; sites that ask for more are not crawled.
- It slows down on 429 and 503 responses and stops crawling a site that answers 403.
- It does not use logins, forms, paywalls or proxies, and fetches only from the published
  addresses.

JavaScript rendering and how long `robots.txt` is cached are not documented.

## User agents

Exact strings, one per line:

```
HyperSearchBot/1.0 (+https://hypersearchbot.ecogpt.com/)
```

This matches the string on EcoGPT's page.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: HyperSearchBot
Disallow: /
```

It follows the `HyperSearchBot` group, or the `*` group when there is none.

## IP ranges and verification

- IP list: https://hypersearchbot.ecogpt.com/hypersearchbot.json, linked from the robot's page,
  which also lists the address. JSON object with `creationTime` and a `prefixes` array of
  `{"ipv4Prefix": ...}` objects. On 2026-11-19 it held one prefix, `34.51.53.27/32`, with
  `creationTime` 2026-11-18.
- Reverse DNS: not documented. On 2026-11-19 the listed address's reverse DNS name was
  `crawl-34-51-53-27.hypersearchbot.ecogpt.com`, which resolves back to it.
- ASN: not documented.
- Web Bot Auth: not documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1, which Hyperwatch 5.7.0 depends on, returns the family
`HyperSearchBot`. In Hyperwatch 5.7.0, `src/modules/identity.js` sets the identity `EcoGPT` for
the family `HyperSearchBot` on a forward-confirmed hostname matching
`crawl-*.hypersearchbot.ecogpt.com` or the published list (`hypersearchbot-ips.json`, 1 prefix,
fetched from the URL above).

The hostname pattern is not documented by EcoGPT; it follows the name its address has.

## Misc

- Contact for problems and removals: dev@ecogpt.com.

## Sources

- https://hypersearchbot.ecogpt.com/ (checked 2026-11-19)
- https://hypersearchbot.ecogpt.com/hypersearchbot.json (checked 2026-11-19)
- https://ecogpt.com/ (checked 2026-11-19)
