---
name: search.marginalia.nu
operator: Marginalia Search
website: https://marginalia-search.com
documentation: https://about.marginalia-search.com/article/crawler/
category: search-engine
robots_txt_token: search.marginalia.nu
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://search.marginalia.nu/crawler-ips.txt
  hostnames: []
hyperwatch:
  family: search.marginalia.nu
  identity: Marginalia
last_checked: 2026-11-19
---

# search.marginalia.nu

## Description

search.marginalia.nu is the crawler of Marginalia Search, an independent, open-source (AGPL)
search engine operating out of Sweden, principally developed and operated by Viktor Lofgren. It
aims to help people discover small and independent websites, and complements the large search
engines rather than replacing them.

## Behavior

Marginalia says the crawler does a full refresh every 8 to 10 weeks. Apart from that, it polls RSS
feeds daily and does some live updates based on what it finds. Sites can ask to be indexed through
https://github.com/MarginaliaSearch/submit-site-to-marginalia-search.

The older webmasters page (2022, now marked "outdated") adds that changes to `robots.txt` may not
take effect immediately, and that the crawler is sometimes blocked by CDNs such as Fastly and
Cloudflare. Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
search.marginalia.nu
```

This matches the user agent given by Marginalia.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: search.marginalia.nu
Disallow: /
```

Marginalia says the crawler looks for the user agent `search.marginalia.nu` specifically, as well
as general directives (`*`). Pages can also be removed by email.

## IP ranges and verification

- IP list: https://search.marginalia.nu/crawler-ips.txt, linked from the crawler page; it
  redirects to https://marginalia-search.com/crawler-ips.txt. Plain text, one address per line. On
  2026-11-19 it held 13 IPv4 addresses, `193.183.0.162` to `193.183.0.174`, and no generation
  date. The crawler page gives the same range, `193.183.0.162-193.183.0.174` (updated 2025-01-07).
- The older webmasters page gives `81.170.128.21, 193.183.0.162-174`. The current page and list
  no longer include `81.170.128.21`.
- Reverse DNS and ASN: not documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1, which Hyperwatch 5.7.0 depends on, returns the family
`search.marginalia.nu`. In Hyperwatch 5.7.0, `src/modules/identity.js` sets the identity
`Marginalia` for the family `search.marginalia.nu` when the address is in the published list
`marginalia-ips.json` (5 prefixes). That list is copied by hand from the older webmasters page:
`81.170.128.21/32` and `193.183.0.162` to `193.183.0.174` as CIDRs.

Where it falls short: Hyperwatch does not read the current list (`crawler-ips.txt`), and keeps
`81.170.128.21`, which only the page marked outdated lists. The 13 current addresses are all
covered.

## Misc

- Contact: contact@marginalia-search.com (the older page gives kontakt@marginalia.nu).
- The search engine's source code is at https://git.marginalia.nu/.

## Sources

- https://about.marginalia-search.com/article/crawler/ (checked 2026-11-19)
- https://about.marginalia-search.com/ (checked 2026-11-19)
- https://search.marginalia.nu/crawler-ips.txt (checked 2026-11-19)
- https://www.marginalia.nu/marginalia-search/for-webmasters/ (checked 2026-11-19)
