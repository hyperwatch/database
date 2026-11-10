---
name: SERankingBacklinksBot
operator: SE Ranking
website: https://seranking.com
documentation: https://help.seranking.com/hc/en-us/articles/23020353159964-SERankingBacklinksBot-Crawler
category: seo
robots_txt_token: SERankingBacklinksBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://api.seranking.com/backlinks-bot-ips
  hostnames: [".seranking.com"]
hyperwatch:
  family: SERankingBacklinksBot
  identity: SE Ranking
last_checked: 2026-11-10
---

# SERankingBacklinksBot

## Description

SERankingBacklinksBot is the link crawler of SE Ranking, an SEO platform. It collects the links on
pages to map how sites link to each other.

## Behavior

SE Ranking says the robot always respects `robots.txt`. Without a `Crawl-delay`, or when
`robots.txt` is missing or does not return status 200, it waits 3 seconds between requests. A
`robots.txt` that does not return 200 is treated as non-existent. After a change to `robots.txt`,
it may take up to a day to stop, because pages may already be queued.

It only collects publicly available pages and stores only their links. JavaScript rendering is
not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SERankingBacklinksBot/1.0; +https://seranking.com/backlinks-crawler)
```

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-10, pages, verified as SE Ranking by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/plain,text/html,application/xhtml+xml,application/xml` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: SERankingBacklinksBot
Disallow: /
```

To slow it down instead:

```
User-agent: SERankingBacklinksBot
Crawl-delay: 10
```

## IP ranges and verification

SE Ranking says the reverse DNS name of the address should be a subdomain of `seranking.com`. It
does not mention a forward lookup.

It also publishes its crawler addresses at https://api.seranking.com/backlinks-bot-ips, as single
addresses, not prefixes. The default is JSON with a `data` array of IPv4 addresses; `?v=6` gives
IPv6 and `?txt=1` gives plain text, one address per line. On 2026-10-15 it held 83 IPv4 and
48 IPv6 addresses. It has no date; SE Ranking says it is always up to date. No ASN is documented.

On 2026-10-15, the first addresses of the IPv4 list had reverse DNS names under
`blex.seranking.com`. SE Ranking does not document that subdomain.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `SERankingBacklinksBot`. In Hyperwatch
`main` (after 5.4.0), `src/modules/identity.js` sets the identity `SE Ranking` on a
forward-confirmed hostname matching `discovery-crawler*.blex.seranking.com` or the published list
(`seranking-ips.json`, the IPv4 and IPv6 responses, 131 addresses). The pattern is narrower than the
documented `seranking.com`: the `blex` subdomain and the `discovery-crawler` prefix come from
observed names, not from SE Ranking's documentation, which does not mention a forward lookup either.

## Misc

The help article was read in a browser: plain HTTP clients got a Cloudflare challenge page. The
URL in the user agent, https://seranking.com/backlinks-crawler, redirects to the help article.
Problems can be reported to the crawler address given in the article.

## Sources

- https://help.seranking.com/hc/en-us/articles/23020353159964-SERankingBacklinksBot-Crawler (checked 2026-10-15)
- https://api.seranking.com/backlinks-bot-ips (checked 2026-10-15)
- https://api.seranking.com/backlinks-bot-ips?v=6 (checked 2026-10-15)
