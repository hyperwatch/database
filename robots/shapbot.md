---
name: ShapBot
operator: Parallel Web Systems
website: https://parallel.ai
documentation: https://parallel.ai/parallel-web-systems-bots
category: ai-search
robots_txt_token: ShapBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://docs.parallel.ai/resources/shapbot.json
  hostnames: []
hyperwatch:
  family: ShapBot
  identity: Parallel
last_checked: 2026-11-10
---

# ShapBot

## Description

ShapBot is the crawler of Parallel Web Systems, which sells web search and extraction APIs for AI
agents. Parallel says ShapBot "collects publicly available web content to build and maintain
Parallel's search index". Restricting it "may reduce your site's visibility and discoverability
through Parallel's web APIs and search features".

## Behavior

Parallel says webmasters "can manage automated access using robots.txt with the User-agent: ShapBot
directive". Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; ShapBot/0.1.0
```

This is the documented string.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-11-10, pages, verified as Parallel by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/markdown, text/html;q=0.9, */*;q=0.8` (63%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/jxl,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` (18%), `*/*` (12%), and 1 other value |
| `accept-language` | `en-US,en;q=0.9` (37%) |
| `priority` | `u=0, i` (18%), `u=1, i` (15%), `i` (4%) |
| `sec-ch-ua` | `"Not:A-Brand";v="8", "Chromium";v="156", "Google Chrome";v="156"` (37%) |
| `sec-ch-ua-mobile` | `?0` (37%) |
| `sec-ch-ua-platform` | `"Linux"` (37%) |
| `sec-fetch-dest` | `document` (18%), `empty` (12%), `image` (7%), and 1 other value |
| `sec-fetch-mode` | `navigate` (18%), `cors` (12%), `no-cors` (7%) |
| `sec-fetch-site` | `none` (18%), `same-origin` (12%), `same-site` (5%), and 1 other value |
| `sec-fetch-storage-access` | `active` (2%) |
| `sec-fetch-user` | `?1` (18%) |
| `signature` | `(present)` (98%) |
| `signature-agent` | `"https://shapbot.parallel.ai"` (98%) |
| `signature-input` | `(present)` (98%) |
| `upgrade-insecure-requests` | `1` (18%) |

## Blocking with robots.txt

```
User-agent: ShapBot
Disallow: /
```

Parallel's other agent, Shap-User, accesses content on behalf of users and "is intended to provide
visibility rather than to be managed through automated controls": Parallel points to ShapBot for
controlling automated crawling.

## IP ranges and verification

Parallel publishes the addresses at https://docs.parallel.ai/resources/shapbot.json: an object with
`creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` objects. On 2026-10-15 it held 10
IPv4 prefixes, all `/32`, with `creationTime` 2026-07-14. No reverse DNS hostname or ASN is
documented. A reverse lookup of three listed addresses on 2026-10-15 returned
`*.bc.googleusercontent.com` names, a Google Cloud suffix shared by all its customers.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ShapBot`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` sets the identity `Parallel` on a cloud hostname ending with
`.googleusercontent.com`, the published list (`shapbot-ips.json`) or a verified signature of
`https://shapbot.parallel.ai` (needs the `webbotauth` module, off by default). The cloud hostname is
not documented by Parallel, and any Google Cloud customer passes it.

## Misc

- Shap-User: `Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; Shap-User/0.1.0`.
  Parallel says it "is not used for crawling the web in an automatic fashion". No list is published
  for it. Hyperwatch parses it as the family `Shap-User` and gives it no identity.
- Parallel's contacts: support@parallel.ai for crawler issues, index@parallel.ai for content
  questions.

## Sources

- https://parallel.ai/parallel-web-systems-bots (checked 2026-10-15)
- https://docs.parallel.ai/resources/crawler (checked 2026-10-15)
- https://docs.parallel.ai/resources/shapbot.json (checked 2026-10-15)
