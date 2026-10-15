---
name: YandexBot
operator: Yandex
website: https://yandex.com
documentation: https://yandex.com/support/webmaster/en/robot-workings/check-yandex-robots
category: search-engine
robots_txt_token: YandexBot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - yandex.ru
    - yandex.net
    - yandex.com
hyperwatch:
  family: YandexBot
  identity: Yandex
last_checked: 2026-10-15
---

# YandexBot

## Description

YandexBot is the main indexing robot of Yandex, the search engine. Yandex runs many other robots
for images, video, ads, previews and other services.

## Behavior

Yandex documents YandexBot as following the general `robots.txt` rules. Its `robots.txt`
documentation lists the directives `User-agent`, `Disallow`, `Allow`, `Sitemap` and `Clean-param`.
`Crawl-delay` is not in that list. Crawl rate is set instead in Yandex Webmaster, as a number of
requests per second; Yandex treats it as a recommendation.

The `robots.txt` file must return HTTP 200 and be at most 500 KB, otherwise the site is treated as
open. Yandex follows redirects of `robots.txt`, including to other sites.

How often `robots.txt` is re-read and whether YandexBot renders JavaScript are not documented on
the pages checked.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; YandexBot/3.0; +http://yandex.com/bots)
```

Yandex also lists `YandexBot/3.0 (MirrorDetector)` among its robots.

## Observed HTTP headers

Only header signatures are available (they keep `accept`, `accept-language` and `dnt`), from fewer than 10 distinct signatures seen on 2026-10-15:

- `accept`: `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8`
- `accept-language`: `ru, tr;q=0.9, be;q=0.8, kk;q=0.7, en;q=0.6, *;q=0.01`
- `dnt`: never sent

## Blocking with robots.txt

```
User-agent: YandexBot
Disallow: /
```

Yandex robots match any `User-agent` line containing the substring `Yandex` (case-insensitive).
`User-agent: Yandex` applies to all Yandex robots; when a `Yandex` group exists, the `*` group is
ignored. Per Yandex's example, `YandexBot` applies only to the main indexing robot.

Some Yandex robots ignore the general rules or `robots.txt` entirely, for example
YandexAccessibilityBot, YandexMobileBot, YandexDirect, YandexFavicons and YandexMetrika.
Yandex says to name such a robot's exact token to address it. `Clean-param` tells Yandex which URL
parameters to ignore.

## IP ranges and verification

None published. Yandex says its robots' addresses change often and the list is not disclosed. The
robots run from AS13238, AS208722 and AS212066.

Verify with reverse DNS: the hostname must end in `yandex.ru`, `yandex.net` or `yandex.com`, and a
forward lookup of that hostname must return the same address. Yandex also offers an IP check tool
in Yandex Webmaster for its indexing robots.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks of the addresses verified by reverse DNS (the operator publishes no ranges):

- AS212066 Buyuk Reklam Cozumleri LLC: `45.148.65.0/24`
- AS13238 YANDEX LLC: `5.255.231.0/24`, `87.250.224.0/24`, `95.108.213.0/24`, `213.180.203.0/24`, `2a02:6b8:c42::/48`

## Hyperwatch

`@hyperwatch/useragent` returns the family `YandexBot`. `src/modules/identity.js` sets the identity
`Yandex` for the families `YandexBot`, `YandexImages`, `YandexMobileBot` and
`YandexAccessibilityBot` when the reverse DNS hostname ends with `.yandex.com`, without the forward lookup Yandex
documents. Hostnames in
`yandex.ru` or `yandex.net`, which Yandex also documents, are not accepted by that rule.

## Misc

Yandex's robot list includes over 40 user agents. Most follow the pattern
`Mozilla/5.0 (compatible; <token>; +http://yandex.com/bots)`.

## Sources

- https://yandex.com/bots (checked 2026-10-15)
- https://yandex.com/support/webmaster/en/robot-workings/check-yandex-robots (checked 2026-10-15)
- https://yandex.com/support/webmaster/en/robot-workings/user-agent (checked 2026-10-15)
- https://yandex.com/support/webmaster/en/controlling-robot/robots-txt (checked 2026-10-15)
- https://yandex.com/support/webmaster/en/service/crawl-rate (checked 2026-10-15)
