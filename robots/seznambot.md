---
name: SeznamBot
operator: Seznam.cz, a.s.
website: https://www.seznam.cz
documentation: https://o-seznam.cz/napoveda/vyhledavani/en/seznambot-crawler/
category: search-engine
robots_txt_token: SeznamBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://search.seznam.cz/ipranges/seznambot.json
  hostnames:
    - .seznam.cz
hyperwatch:
  family: SeznamBot
  identity: Seznam
last_checked: 2026-10-15
---

# SeznamBot

## Description

SeznamBot is the web crawler of Seznam.cz, a Czech search engine. It retrieves content for the
Seznam search index.

## Behavior

Seznam says SeznamBot "fully complies" with `robots.txt`. It typically takes several days for the
crawler to recheck `robots.txt` and update the index, and up to several weeks for sites it visits
rarely.

SeznamBot supports a `Request-rate` directive (for example `Request-rate: 1/10 s`, optionally
limited to a time of day in UTC). The minimum rate is one document every 10 seconds: a lower value
is read as that minimum. `Crawl-delay` is not mentioned. It obeys the `noindex` and `nofollow`
robots meta tags and `rel="nofollow"` links, and reads sitemaps.

The page also names FreshBot, "a fast crawler designed to index pages and RSS feeds containing
fresh content", without giving its user agent. JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SeznamBot/4.0; +https://o-seznam.cz/napoveda/vyhledavani/en/seznambot-crawler/)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SeznamBot
Disallow: /
```

Besides the standard, SeznamBot recognizes `Allow`, the wildcards `*` and `$`, `Request-rate` and
`Sitemap`.

## IP ranges and verification

Seznam lists the crawler's addresses on its help page: `77.75.76.x` to `77.75.79.x` and two IPv6
ranges for SeznamBot, other addresses for a test version, and two addresses from which it verifies
IndexNow keys.

The same addresses are published as JSON at https://search.seznam.cz/ipranges/seznambot.json, an
object with `creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` or `{"ipv6Prefix": ...}`
objects. On 2026-10-15 it held 92 entries (46 IPv4 `/32` addresses, 46 IPv6 `/123` prefixes, all in
`2a02:598::/32`) and was dated 2026-07-13.

All SeznamBot addresses should have a reverse DNS name such as
`fulltextrobot-77-75-77-xxx.seznam.cz` (`fulltextrobot-test-…` for the test version). The page does
not say to confirm the name with a forward lookup. `2a02:598::/32` is registered to Seznam.cz, a.s.
(AS43037) in the RIPE database.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SeznamBot`. In Hyperwatch `main` (after 5.3.3),
`src/modules/identity.js` sets the identity `Seznam` on an unconfirmed hostname ending with
`.seznam.cz`, the inline range `2a02:598::/32` or the published list (`seznambot-ips.json`). The
inline range is Seznam's whole IPv6 allocation, wider than the published crawler prefixes. The
hostname is not confirmed with a forward lookup, which Seznam does not mention either.

## Misc

Nothing else documented.

## Sources

- https://o-seznam.cz/napoveda/vyhledavani/en/seznambot-crawler/ (checked 2026-10-15)
- https://o-seznam.cz/napoveda/vyhledavani/en/crawling-control/ (checked 2026-10-15)
- https://o-seznam.cz/napoveda/vyhledavani/en/indexing-control/ (checked 2026-10-15)
- https://search.seznam.cz/ipranges/seznambot.json (checked 2026-10-15)
- RIPE database entry for `2a02:598::/32` (checked 2026-10-15)
