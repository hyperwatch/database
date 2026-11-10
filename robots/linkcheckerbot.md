---
name: LinkCheckerBot
operator: LinkChecker.pro
website: https://linkchecker.pro
documentation: https://linkchecker.pro/robot/
category: seo
robots_txt_token: LinkCheckerBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://linkchecker.pro/robot-ips
  hostnames: []
hyperwatch:
  family: LinkCheckerBot
  identity: LinkChecker
last_checked: 2026-11-10
---

# LinkCheckerBot

## Description

LinkCheckerBot is the crawler of LinkChecker.pro, a backlink monitoring service. It checks the
backlinks of LinkChecker.pro's users.

## Behavior

LinkChecker.pro says LinkCheckerBot obeys `robots.txt` and `Crawl-delay`. Crawl rate, JavaScript
rendering and how often `robots.txt` is read are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; LinkCheckerBot/2.0; +https://linkchecker.pro/robot/)
```

## Observed HTTP headers

Based on dozens of requests seen on 2026-11-09 and 2026-11-10, all for pages' resources, from a
published address. Nine in ten were image requests (`sec-fetch-dest: image`) with the headers a
Chromium browser sends while loading a page, which suggests the pages are rendered in a browser;
LinkChecker.pro does not document it.

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (91%), `*/*` (5%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` (5%) |
| `accept-language` | `en-US,en;q=0.9` (100%) |
| `priority` | `i` (81%), `u=1, i` (14%), `u=0, i` (5%) |
| `sec-fetch-dest` | `image` (91%), `document` (5%), `empty` (5%) |
| `sec-fetch-mode` | `no-cors` (91%), `cors` (5%), `navigate` (5%) |
| `sec-fetch-site` | `cross-site` (78%), `same-site` (13%), `none` (5%), `same-origin` (5%) |
| `sec-fetch-storage-access` | `active` (78%) |
| `sec-fetch-user` | `?1` (5%) |
| `upgrade-insecure-requests` | `1` (5%) |

No `sec-ch-ua` client hints were sent.

## Blocking with robots.txt

```
User-agent: LinkCheckerBot
Disallow: /
```

`Crawl-delay` in the same group sets the minimum delay between two requests.

## IP ranges and verification

LinkChecker.pro publishes its addresses at https://linkchecker.pro/robot-ips, linked as "IP address
range" from the documentation page: plain text, one address per line. On 2026-11-10 it held 4 IPv4
addresses and no date. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-11-09 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Reverse DNS hostnames:

- `*.clients.your-server.de` (forward-confirmed, addresses in the published list): Hetzner's
  default names, not specific to LinkChecker.pro.

## Hyperwatch

`@hyperwatch/useragent` returns the family `LinkCheckerBot`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` sets the identity `LinkChecker` when the address is in the published list
(`linkcheckerbot-ips.json`, fetched by `node scripts/fetch-ips.js` from
https://linkchecker.pro/robot-ips: 4 addresses, the same as the published list on 2026-11-10).

## Misc

Nothing else documented.

## Sources

- https://linkchecker.pro/robot/ (checked 2026-11-10)
- https://linkchecker.pro/robot-ips (checked 2026-11-10)
