---
name: ev-crawler
operator: Headline
website: https://headline.com
documentation: https://headline.com/web-crawler/
category: other
robots_txt_token: ev-crawler
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: ev-crawler
  identity: Headline
last_checked: 2026-11-10
---

# ev-crawler

## Description

ev-crawler is the crawler of Headline, a venture capital firm. Headline says it visits websites
"every so often" for publicly available information such as home page content, job postings, team
pages and location references, because it is "constantly searching the world for interesting
companies".

## Behavior

Not documented beyond the description above.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ev-crawler/1.0; +https://headline.com/web-crawler)
```

Headline's page does not give the user agent. This string comes from Known Agents. The URL
`https://headline.com/legal/crawler` redirects to the same page.

## Observed HTTP headers

Based on dozens of requests seen on 2026-11-10, pages, verified as Headline by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (97%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/jxl,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` (1%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` (1%) |
| `accept-language` | `en-US,en;q=0.9` (100%) |
| `priority` | `i` (95%), `u=0, i` (3%), `u=2, i` (3%) |
| `sec-ch-ua` | `"Chromium";v="151", "Not=A?Brand";v="99"` (99%), `"Not:A-Brand";v="8", "Chromium";v="156"` (1%) |
| `sec-ch-ua-mobile` | `?0` (100%) |
| `sec-ch-ua-platform` | `"Linux"` (100%) |
| `sec-fetch-dest` | `image` (97%), `document` (3%) |
| `sec-fetch-mode` | `no-cors` (97%), `navigate` (3%) |
| `sec-fetch-site` | `cross-site` (85%), `same-site` (12%), `none` (3%) |
| `sec-fetch-storage-access` | `none` (85%) |
| `sec-fetch-user` | `?1` (3%) |
| `upgrade-insecure-requests` | `1` (3%) |

## Blocking with robots.txt

```
User-agent: ev-crawler
Disallow: /
```

The token is taken from the user agent. Headline does not mention `robots.txt`. It asks site owners
who would prefer not to be crawled to write to the address on its page.

## IP ranges and verification

None published. No hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `ev-crawler`. In Hyperwatch `main`
(after 5.4.0), `src/modules/identity.js` sets the identity `Headline` on the forward-confirmed
hostname `*.core.headline.com`. Headline documents no hostname: the pattern is Hyperwatch's own.

## Misc

Nothing else documented.

## Sources

- https://headline.com/web-crawler/ (checked 2026-10-15, reached from https://headline.com/legal/crawler)
- https://knownagents.com/agents/ev-crawler (checked 2026-10-15)
