---
name: YouBot
operator: You.com
website: https://you.com
documentation: https://you.com/docs/youbot
category: search-engine
robots_txt_token: YouBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: null
  hostnames:
    - .search.you.com
hyperwatch:
  family: YouBot
  identity: You.com
last_checked: 2026-10-16
---

# YouBot

## Description

YouBot is the web crawler of You.com. The operator describes it as the crawler that powers the
You.com search engine.

## Behavior

You.com says YouBot respects `robots.txt`, including user-agent specific rules and `Crawl-delay`.
It caches `robots.txt` for 30 minutes, so changes can take up to 30 minutes to apply.

It uses adaptive crawl rate limiting and spreads requests across several IP addresses. A `429`
response makes it reduce its crawl rate. A `503` response pauses crawling for a while. Excessive
activity can be reported to spider@you.com.

JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; YouBot/1.0; +https://you.com/bot)
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; YouBot/1.0; +https://docs.you.com/youbot; env:prod) Chrome/142.0.0.0 Safari/537.36
```

The operator documents the second form, with `X.X.X.X` standing for the Chrome version. The
`env:prod` part marks production traffic.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as You.com by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exch` (100%) |
| `cache-control` | `no-cache` (100%) |
| `pragma` | `no-cache` (100%) |
| `priority` | `u=0, i` (100%) |
| `sec-ch-ua` | `"HeadlessChrome";v="153", "Not_A Brand";v="8", "Chromium";v="153"` (100%) |
| `sec-ch-ua-mobile` | `?0` (100%) |
| `sec-ch-ua-platform` | `"Linux"` (100%) |
| `sec-fetch-dest` | `document` (100%) |
| `sec-fetch-mode` | `navigate` (100%) |
| `sec-fetch-site` | `none` (100%) |
| `sec-fetch-user` | `?1` (100%) |
| `upgrade-insecure-requests` | `1` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: YouBot
Disallow: /
```

`Crawl-delay` is supported, for example `Crawl-delay: 10`.

## IP ranges and verification

You.com says real YouBot requests come from `68.67.112.0/24`. It does not publish a separate IP
list file.

Reverse DNS follows the pattern `youbot-{octets-with-hyphens}.search.you.com`, for example
`68.67.112.106` resolves to `youbot-68-67-112-106.search.you.com`. A forward lookup of that name
must return the same address.

You.com also recommends cryptographic verification with Web Bot Auth (HTTP message signatures,
Ed25519 keys in JWK format). The public keys are at
https://you.com/.well-known/http-message-signatures-directory. No ASN is documented.


## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `YouBot`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `You.com` on an unconfirmed hostname ending with
`.search.you.com` or the inline range `68.67.112.0/24`. It does not do the forward lookup You.com
documents, and does not check Web Bot Auth signatures.

## Misc

The documentation moved from https://docs.you.com/youbot (still in the user agent) to
https://you.com/docs/youbot. The URL https://you.com/bot in the older user agent leads to a
sign-in page.

## Sources

- https://you.com/docs/youbot (checked 2026-10-15)
- https://docs.you.com/youbot (checked 2026-10-15)
