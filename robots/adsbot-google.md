---
name: AdsBot-Google
operator: Google
website: https://ads.google.com
documentation: https://developers.google.com/crawling/docs/crawlers-fetchers/google-special-case-crawlers
category: marketing
robots_txt_token: AdsBot-Google
respects_robots_txt: partial
verification:
  method: both
  ip_list: https://developers.google.com/static/crawling/ipranges/special-crawlers.json
  hostnames:
    - "rate-limited-proxy-*.google.com"
hyperwatch:
  family: AdsBot-Google
  identity: Google Special Crawlers
last_checked: 2026-11-10
---

# AdsBot-Google

## Description

AdsBot-Google is one of Google's special-case crawlers. Google says it checks the quality of the
web pages that Google Ads ads link to. AdsBot-Google-Mobile is its mobile variant, with its own
`robots.txt` token, in the same documentation.

## Behavior

Google says special-case crawlers are "used by specific products where there's an agreement
between the crawled site and the product", may ignore `robots.txt` rules, and so operate from a
different IP range than its common crawlers. Crawl rate, `Crawl-delay` support and JavaScript
rendering are not documented on that page.

## User agents

Exact strings, one per line:

```
AdsBot-Google (+http://www.google.com/adsbot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/W.X.Y.Z Mobile Safari/537.36 (compatible; AdsBot-Google-Mobile; +http://www.google.com/mobile/adsbot.html)
```

Google writes `W.X.Y.Z` for the Chrome version, which changes.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: AdsBot-Google
Disallow: /

User-agent: AdsBot-Google-Mobile
Disallow: /
```

Google says AdsBot-Google and AdsBot-Google-Mobile ignore the global user agent (`*`) group: they
must be named to be blocked.

## IP ranges and verification

Google publishes the special-case crawlers' addresses at
https://developers.google.com/static/crawling/ipranges/special-crawlers.json, in the Googlebot
format (`creationTime` and a `prefixes` array of `ipv4Prefix` / `ipv6Prefix` objects). On
2026-11-10 it held 272 prefixes, with `creationTime` 2026-11-09.

Reverse DNS: Google gives the mask `rate-limited-proxy-***-***-***-***.google.com` for
special-case crawlers, to be confirmed by a forward lookup back to the same address.

## Hyperwatch

`@hyperwatch/useragent` returns the families `AdsBot-Google` and `AdsBot-Google-Mobile`. In
Hyperwatch `main` (after 5.4.0), `src/modules/identity.js` has no rule for these families: when no
other rule set an identity, it sets `Google Special Crawlers` for any request whose address is in
the published list (`google-special-crawlers-ips.json`, fetched from Google's special-crawlers.json)
or whose forward-confirmed hostname matches `rate-limited-proxy-*.google.com`, whatever the user
agent. Both follow Google's documentation. The identity covers all of Google's special-case crawlers
(APIs-Google, Google-Safety, Mediapartners-Google…), not only AdsBot.

## Misc

Google's other special-case crawlers are APIs-Google, Google-Safety and Mediapartners-Google; Google
lists AdsBot Mobile Web, Duplex on the web, Google Favicon, Mobile Apps Android and Web Light as
retired. Its common crawlers are [Googlebot](googlebot.md) and others, and its user-triggered
fetchers include [GoogleDocs](googledocs.md) and [GoogleImageProxy](googleimageproxy.md).

## Sources

- https://developers.google.com/crawling/docs/crawlers-fetchers/google-special-case-crawlers (checked 2026-11-10)
- https://developers.google.com/crawling/docs/crawlers-fetchers/overview-google-crawlers (checked 2026-11-10)
- https://developers.google.com/static/crawling/ipranges/special-crawlers.json (checked 2026-11-10)
