---
name: coccocbot
operator: Cốc Cốc Company Limited
website: https://coccoc.com
documentation: https://coccoc.com/search/console/en/coc-coc-robots
category: search-engine
robots_txt_token: coccocbot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - .coccoc.com
hyperwatch:
  family: Coc Coc Bot Web
  identity: Coc Coc
last_checked: 2026-10-15
---

# coccocbot

## Description

Cốc Cốc robots are the crawlers of the Cốc Cốc search engine (Vietnam). They discover and download
pages to include them in the Cốc Cốc index. `coccocbot` is the generic name for all of them;
`coccocbot-web` is the main web robot and `coccocbot-image` the image robot. Cốc Cốc also lists
`coccocbot-fast` (fast robot), `coccocbot-ads` (ads) and `coccocbot-shopping` (e-commerce sites).

## Behavior

Before requesting other URLs from a site, a Cốc Cốc robot requests `robots.txt` over HTTP or HTTPS,
following up to 5 redirects. If it gets no response, the site is treated as unavailable and left out
of crawling for a while. Any response other than `200 OK` means unrestricted access. The directives
are used until the next time it fetches `robots.txt`; how often that happens is not documented.

`Crawl-delay` is supported, in whole seconds, up to 10 seconds: a larger value is treated as 10.
`noindex` directives are covered on a separate page. JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; coccocbot/1.0; +http://help.coccoc.com/searchengine)
Mozilla/5.0 (compatible; coccocbot-web/1.0; +http://help.coccoc.com/searchengine)
coccocbot-web/1.0 (+http://help.coccoc.com/searchengine)
Mozilla/5.0 (compatible; coccocbot-image/1.0; +http://help.coccoc.com/searchengine)
Mozilla/5.0 (compatible; coccocbot-fast/1.0; +http://help.coccoc.com/searchengine)
Mozilla/5.0 (compatible; coccocbot-ads/1.0; +http://help.coccoc.com/searchengine)
Mozilla/5.0 (compatible; coccocbot-shopping/1.0; +http://help.coccoc.com/searchengine)
```

The short `coccocbot-web/1.0` string is used "in some cases" instead of the `Mozilla/5.0` one.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: coccocbot
Disallow: /
```

`coccocbot` applies to all Cốc Cốc robots. Each robot uses the `User-agent` group that matches its
name most closely, so `coccocbot-web` or `coccocbot-image` groups override the `coccocbot` group
for those robots. `Allow`, `*`, `$`, `Sitemap` and `Crawl-delay` (10 seconds at most) are
supported. When `Allow` and `Disallow` are equally specific, `Allow` wins.

## IP ranges and verification

Cốc Cốc documents a forward-confirmed reverse DNS check: the reverse DNS name must end with
`.coccoc.com`, and that name must resolve back to the same address. No IP list or ASN is published.

## Hyperwatch

`@hyperwatch/useragent` returns the families `Coc Coc Bot` (`coccocbot`), `Coc Coc Bot Web` (both
`coccocbot-web` strings) and `Coc Coc Bot Image`. `coccocbot-fast`, `coccocbot-ads` and
`coccocbot-shopping` parse as their own token (`coccocbot-fast` and so on).

`src/modules/identity.js` sets the identity `Coc Coc` for the first three families when the
unconfirmed hostname ends with `.coccoc.com`. Cốc Cốc documents a forward-confirmed check; the rule
does not use the confirmed hostname. The fast, ads and shopping robots have no rule, so they get no
identity.

## Misc

The pages were last updated on 15/07/2022, according to their own dates.

## Sources

- https://coccoc.com/search/console/en/coc-coc-robots (checked 2026-10-15; https://help.coccoc.com/en/search-engine/coccoc-robots redirects there)
- https://coccoc.com/search/console/en/robots.txt (checked 2026-10-15)
- https://coccoc.com/search/console/en/handle-overload-of-website-due-to-coc-coc-robot (checked 2026-10-15)
