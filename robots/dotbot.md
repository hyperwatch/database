---
name: DotBot
operator: Moz
website: https://moz.com
documentation: https://moz.com/help/moz-procedures/crawlers/dotbot
category: seo
robots_txt_token: dotbot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: DotBot
  identity: Moz
last_checked: 2026-10-15
---

# DotBot

## Description

DotBot is the web crawler of Moz. It gathers the data of the Moz Link Index, used by Link
Explorer, the Links section of Moz Pro campaigns and the Moz API. Moz's site audit crawler is a
different robot, Rogerbot.

## Behavior

Moz says DotBot always respects `robots.txt`, and gives `Crawl-delay` as the way to slow it down.
It reads `robots.txt` only the first time it meets a site during a new index crawl: a change is
not seen until the next time Moz finds links to the site.

Crawl rate, JavaScript rendering and what it fetches besides pages are not documented.

## User agents

Moz's page gives only the token `dotbot`, not a full user agent string. The link
https://opensiteexplorer.org/dotbot redirects to the documentation page.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: dotbot
Disallow: /
```

To slow it down instead:

```
User-agent: dotbot
Crawl-delay: 10
```

## IP ranges and verification

None published. Moz documents no IP list, reverse DNS name or ASN.

## Hyperwatch

With no documented user agent string, the agent family could not be checked with
`@hyperwatch/useragent`. `src/modules/identity.js` sets the identity `Moz` for the family
`DotBot` when the address is in the inline range `216.244.64.0/19`. Moz does not document this
range. According to ARIN's registration data, it is registered to Wowrack.com, a hosting
provider, so other customers of that network would pass the check.

## Misc

Moz's Performance Metrics data comes from Google Lighthouse's crawler (`Chrome-Lighthouse`), not
from DotBot.

## Sources

- https://moz.com/help/moz-procedures/crawlers/dotbot (checked 2026-10-15)
- https://rdap.arin.net/registry/ip/216.244.64.0/19 (checked 2026-10-15)
