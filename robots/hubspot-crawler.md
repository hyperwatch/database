---
name: HubSpot Crawler
operator: HubSpot
website: https://www.hubspot.com
documentation: https://knowledge.hubspot.com/seo/understand-seo-crawling-errors
category: seo
robots_txt_token: HubSpot Crawler
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://api.hubapi.com/meta/network-origins/2026-09/ip-ranges
  hostnames: []
hyperwatch:
  family: HubSpot Crawler
  identity: null
last_checked: 2026-10-15
---

# HubSpot Crawler

## Description

HubSpot Crawler is the crawler of HubSpot, a marketing, sales and customer service platform.
HubSpot's own documentation mentions it for the SEO tool, which scans pages of its customers'
sites and reports crawl errors. Third-party directories also describe it as a fetcher that reads
page metadata when a URL is shared in HubSpot; HubSpot does not document this.

## Behavior

HubSpot reports "Scan blocked by robots.txt file" and "Robots.txt file couldn't be retrieved" as
SEO crawl errors, so the SEO scans read and follow `robots.txt`. Crawl rate, `Crawl-delay`
support, JavaScript rendering and `robots.txt` caching are not documented.

## User agents

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; HubSpot Crawler; +https://www.hubspot.com) Chrome/131.0.0.0 Safari/537.36
```

HubSpot only documents the name `HubSpot Crawler`, not the full string.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: HubSpot Crawler
Disallow: /
```

HubSpot tells customers to add "HubSpot Crawler" as an exemption in `robots.txt` when their scans
are blocked. Known Agents says it is not expected to follow `robots.txt`, which conflicts with
HubSpot's documentation.

## IP ranges and verification

HubSpot publishes the addresses its tools use through a public API, without authentication:
https://api.hubapi.com/meta/network-origins/2026-09/ip-ranges (also under `2026-03`). The JSON
response has a `results` array of objects with `cidr`, `direction`, `service` and `description`.
A plain text variant is at `/meta/network-origins/2026-09/ip-ranges/simple` with
`Accept: text/plain`.

When checked, it listed 36 IPv4 ranges with `service: WEB_SCRAPING` (description "Web crawling and
user-generated traffic"), next to `API`, `DNS` and `EMAIL` ranges. The list is not specific to
HubSpot Crawler: it covers all of HubSpot's crawling and user-generated traffic. HubSpot says the
ranges change over time and should be fetched regularly.

No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `HubSpot Crawler`. `src/modules/identity.js`
has no rule for it, so it gets no identity.

## Misc

Other HubSpot user agents reported by third parties include `HubSpot Links Crawler 2.0`,
`HubSpot Page Fetcher` and `HubSpot-FeedFetcher`.

## Sources

- https://knowledge.hubspot.com/seo/understand-seo-crawling-errors (checked 2026-10-15)
- https://developers.hubspot.com/docs/api-reference/latest/account/ip-ranges/guide.md (checked 2026-10-15)
- https://api.hubapi.com/meta/network-origins/2026-09/ip-ranges (checked 2026-10-15)
- https://knownagents.com/agents/hubspot-crawler (checked 2026-10-15)
- https://community.hubspot.com/t5/APIs-Integrations/HubSpot-Links-Crawler-2-0-user-agent-hitting-protected-pages/m-p/229544 (checked 2026-10-15)
