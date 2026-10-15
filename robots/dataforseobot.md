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
last_checked: 2026-10-15
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

No requests from this robot were captured with their headers yet.

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

`@hyperwatch/useragent` parses the string above as family `DataForSeoBot`. Hyperwatch sets the
identity `DataForSeo` when the unconfirmed hostname ends with `.dataforseo.com`. It does not
confirm the hostname with a forward lookup and does not use the published subnets.

## Misc

Nothing else documented.

## Sources

- https://dataforseo.com/dataforseo-bot (checked 2026-10-15)
