---
name: MegaIndex.ru
operator: MegaIndex
website: https://www.megaindex.ru
documentation: https://ru.megaindex.com/crawler
category: seo
robots_txt_token: "*"
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: MegaIndex.ru
  identity: MegaIndex.ru
last_checked: 2026-10-15
---

# MegaIndex.ru

## Description

MegaIndex.ru is the crawler of MegaIndex, a Russian SEO service. Its page (in Russian) says
"MegaIndex indexes links on websites all over the world", for its backlink analysis tools.
The page names it "MegaIndex Crawler" and gives no legal entity, only "© MegaIndex 2008 - 2026".
The footer of megaindex.com names MegaIndex Limited, Hong Kong.

## Behavior

MegaIndex says the crawler uses the `Crawl-delay` value from `robots.txt`, up to 5 seconds.
Crawl rate without `Crawl-delay`, JavaScript rendering and `robots.txt` caching are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; MegaIndex.ru/2.0; +http://megaindex.com/crawler)
Mozilla/5.0 (compatible; MegaIndex.ru/2.0; +https://www.megaindex.ru/?tab=linkAnalyze)
```

MegaIndex does not publish its user agent. These strings come from the crawler-user-agents list.
On 2026-10-15, `http://megaindex.com/crawler` redirected to the megaindex.com home page, which
has no crawler information; the crawler page is at `https://ru.megaindex.com/crawler`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: *
Disallow: /
```

MegaIndex says it supports `robots.txt` restrictions for `User-agent: *`. Whether it obeys a
record naming it (`User-agent: MegaIndex.ru` or `MegaIndex`) is not documented. To slow it down,
`Crawl-delay` is honored up to 5 seconds.

## IP ranges and verification

None published. No IP list, reverse DNS names or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `MegaIndex.ru` for both strings.
`src/modules/identity.js` sets the identity `MegaIndex.ru` when the unconfirmed hostname ends
with `.clients.your-server.de`. This is a cloud hostname, the default reverse DNS of Hetzner
servers: any Hetzner customer passes. MegaIndex does not document running on Hetzner.

## Misc

The page gives a contact form and phone numbers for questions about the crawler.

## Sources

- https://ru.megaindex.com/crawler (checked 2026-10-15)
- https://megaindex.com/crawler (redirects to the home page, checked 2026-10-15)
- https://raw.githubusercontent.com/monperrus/crawler-user-agents/master/crawler-user-agents.json (checked 2026-10-15)
