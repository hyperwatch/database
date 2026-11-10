---
name: TikTokSpider
operator: TikTok (ByteDance), by its user agent; not confirmed by TikTok documentation
website: https://www.tiktok.com
documentation: null
category: unknown
robots_txt_token: TikTokSpider
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: TikTokSpider
  identity: TikTok
last_checked: 2026-11-10
---

# TikTokSpider

## Description

TikTokSpider is a robot whose user agent gives a `tiktok.com` contact address. No TikTok or
ByteDance page describing it was found: searches for the robot name and for its contact address
returned only third-party bot directories. According to Known Agents, it is a TikTok fetcher that
fetches pages "when users share external links" to collect metadata and thumbnails for link
previews. This is not confirmed by TikTok.

## Behavior

Not documented by the operator: request rate, `Crawl-delay` support, JavaScript rendering and
`robots.txt` caching are unknown.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Linux; Android 5.0) AppleWebKit/537.36 (KHTML, like Gecko) Mobile Safari/537.36 (compatible; TikTokSpider; ttspider-feedback@tiktok.com)
```

This string comes from Known Agents, not from TikTok.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-10, pages, verified as TikTok by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/heif,image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (100%) |
| `accept-language` | `en-US,en;q=0.5` (100%) |
| `priority` | `u=1, i` (100%) |
| `sec-fetch-dest` | `image` (100%) |
| `sec-fetch-mode` | `no-cors` (100%) |
| `sec-fetch-site` | `same-site` (100%) |

## Blocking with robots.txt

```
User-agent: TikTokSpider
Disallow: /
```

The token is the name in the user agent. TikTok does not document whether it obeys `robots.txt`.
Known Agents says it is not expected to follow `robots.txt` rules.

## IP ranges and verification

None published. TikTok does not document an IP list, reverse DNS names or an ASN for TikTokSpider.

## Hyperwatch

`@hyperwatch/useragent` returns the family `TikTokSpider`. In `src/modules/identity.js`, Hyperwatch
sets the identity `TikTok` when the reverse DNS hostname (not forward-confirmed) ends with
`.crawl.bytedance.com` or `.ap-southeast-1.compute.amazonaws.com`, the same rule as for Bytespider.
Neither suffix is documented by TikTok or ByteDance. The second is a cloud hostname: it matches any
AWS EC2 instance in the Singapore region, so it does not prove that a request comes from TikTok.

## Misc

- ByteDance's Bytespider has its own file.
- TikTok's own `robots.txt` does not mention TikTokSpider.

## Sources

- https://knownagents.com/agents/tiktokspider (checked 2026-10-15; https://darkvisitors.com/agents/tiktokspider redirects there)
- https://www.tiktok.com/robots.txt (checked 2026-10-15)
