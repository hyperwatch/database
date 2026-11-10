---
name: DataForSeoBot
operator: DataForSEO
website: https://dataforseo.com
documentation: https://dataforseo.com/dataforseo-bot
category: seo
robots_txt_token: DataForSeoBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://dataforseo.com/dataforseo-bot
  hostnames: [".dataforseo.com"]
hyperwatch:
  family: DataForSeoBot
  identity: DataForSeo
last_checked: 2026-11-10
---

# DataForSeoBot

## Description

DataForSeoBot, which DataForSEO also calls "DataForSEO Link Bot", crawls the web for the backlink
database behind DataForSEO's Backlinks API.

## Behavior

DataForSEO says the robot adds the links it finds on a page to its backlink database and checks
links already in it. It says the robot collects no other data from the site.

It obeys `robots.txt`, including wildcards (`*`), and `Crawl-delay`. Its default is one visit
every 5 seconds. The documentation page has a form to make the robot reload a site's
`robots.txt`. JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; DataForSeoBot; +https://dataforseo.com/dataforseo-bot)
```

The page gives the version as 1.0, but the string above has no version number.

## Observed HTTP headers

Based on dozens of requests seen on 2026-11-10, pages, verified as DataForSeo by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept-language` | `*` (100%) |
| `upgrade-insecure-requests` | `1` (100%) |

Never sent: `accept`.

## Blocking with robots.txt

```
User-agent: DataForSeoBot
Disallow: /
```

To slow it down instead:

```
User-agent: DataForSeoBot
Crawl-delay: 5
```

## IP ranges and verification

DataForSEO lists its subnets on the documentation page itself, as text: on 2026-10-15, 3 IPv4
`/29` prefixes and 3 IPv6 `/64` prefixes. The list has no date. No separate file and no ASN are
published.

It also documents reverse DNS: names follow the mask `crawling-gateway-*.dataforseo.com`, for
example `crawling-gateway-136-243-228-176.dataforseo.com`. It does not say to confirm the name
with a forward lookup.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `DataForSeoBot`. In Hyperwatch `main`
(after 5.4.0), `src/modules/identity.js` sets the identity `DataForSeo` on the forward-confirmed
hostname `crawling-gateway-*.dataforseo.com` or the published list `dataforseo-ips.json` (the
3 IPv4 `/29` and 3 IPv6 `/64` prefixes from the documentation page, copied by hand, so it is not
refreshed when the page changes). The forward lookup is Hyperwatch's own addition: DataForSEO does
not ask for it.

## Misc

Nothing else documented.

## Sources

- https://dataforseo.com/dataforseo-bot (checked 2026-10-15)
