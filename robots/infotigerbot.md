---
name: InfoTigerBot
operator: Infotiger UG (haftungsbeschränkt)
website: https://infotiger.com
documentation: https://infotiger.com/bot.html
category: search-engine
robots_txt_token: InfoTigerBot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - .infotiger.com
hyperwatch:
  family: InfoTigerBot
  identity: InfoTiger
last_checked: 2026-10-15
---

# InfoTigerBot

## Description

InfoTigerBot is the crawler of Infotiger, a search engine run by Infotiger UG
(haftungsbeschränkt) from Taufkirchen, Germany. It retrieves pages that may be parsed and indexed in
the Infotiger search engine.

## Behavior

Infotiger says the robot "limits the number of requests per minute to a single host". It obeys
`robots.txt` and the `noindex` and `nofollow` robots meta tags. `Crawl-delay` support, JavaScript
rendering and `robots.txt` caching are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; InfoTigerBot/1.9; +https://infotiger.com/bot)
```

Infotiger says the robot is "usually" identified by this string. The URL in it,
`https://infotiger.com/bot`, returned 404 on 2026-10-15; the documentation is at
`https://infotiger.com/bot.html`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: InfoTigerBot
Disallow: /
```

The page gives no `robots.txt` example; the token above is the robot's name. Problems go to
contact (at) infotiger (dot) com.

## IP ranges and verification

Infotiger documents a forward-confirmed reverse DNS check: crawler addresses resolve to names such
as `crawler-40-88-143-91.infotiger.com`, which must resolve back to the same address. No IP list or
ASN is published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `InfoTigerBot`. `src/modules/identity.js` sets the
identity `InfoTiger` when the unconfirmed hostname ends with `.infotiger.com`. Infotiger documents a
forward-confirmed check; the rule does not use the confirmed hostname.

## Misc

Sites can submit URLs to be crawled through https://infotiger.com/addurl.html.

## Sources

- https://infotiger.com/bot.html (checked 2026-10-15)
- https://infotiger.com/bot (checked 2026-10-15, 404)
- https://infotiger.com/company.html (checked 2026-10-15)
