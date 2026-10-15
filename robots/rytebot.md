---
name: RyteBot
operator: Semrush (formerly Ryte GmbH, acquired by Semrush in 2024)
website: https://en.ryte.com
documentation: https://www.semrush.com/bot/
category: seo
robots_txt_token: RyteBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: RyteBot
  identity: Semrush
last_checked: 2026-10-15
---

# RyteBot

## Description

RyteBot is the crawler of Ryte, a Munich website quality and SEO platform. Semrush announced on
2024-07-12 that it had completed the acquisition of Ryte, and planned to integrate "Ryte's
advanced crawling technology" into its Enterprise SEO platform. Semrush's bot page now lists
RyteBot among its crawlers, used for "the tools provided by Ryte.com, which analyze on-page SEO,
technical and usability issues". The crawler's former page, `https://bot.ryte.com/`, redirects to
Semrush's bot page.

## Behavior

Not documented beyond its purpose. Crawl rate, `Crawl-delay` support, JavaScript rendering and
`robots.txt` caching are not documented for RyteBot. The crawl-delay and caching rules on
Semrush's page are given for SemrushBot only.

## User agents

Exact strings, one per line:

```
RyteBot/1.0.0 (+https://bot.ryte.com/)
```

Semrush publishes only the `robots.txt` token. This string comes from the crawler-user-agents
list.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: RyteBot
Disallow: /
```

Semrush gives this record "to block RyteBot from crawling your site for tools provided by
Ryte.com". The other Semrush tokens must be blocked separately: see `semrushbot.md`.

## IP ranges and verification

None published for RyteBot. Semrush's bot page documents no IP list or reverse DNS method for it.

## Hyperwatch

`@hyperwatch/useragent` returns the family `RyteBot`. `src/modules/identity.js` sets the identity
`Semrush` when the forward-confirmed hostname ends with `.semrush.com`, or when the address is in
the inline range `85.208.98.0/24`. Semrush documents neither for RyteBot: the hostname suffix is
not documented for any Semrush crawler, and the only documented range, `85.208.98.128/25`, is for
Site Audit. Whether RyteBot crawls from Semrush's network or from Ryte's former one is not
documented.

## Misc

Ryte's site, `https://en.ryte.com`, was still online on 2026-10-15.

## Sources

- https://www.semrush.com/bot/ (checked 2026-10-15)
- https://bot.ryte.com/ (redirects to the Semrush bot page, checked 2026-10-15)
- https://en.ryte.com/company/newsroom/ryte-announces-acquisition-by-semrush/ (checked 2026-10-15)
- https://raw.githubusercontent.com/monperrus/crawler-user-agents/master/crawler-user-agents.json (checked 2026-10-15)
