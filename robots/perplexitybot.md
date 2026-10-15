---
name: PerplexityBot
operator: Perplexity AI
website: https://www.perplexity.ai
documentation: https://docs.perplexity.ai/guides/bots
category: ai-search
robots_txt_token: PerplexityBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://www.perplexity.com/perplexitybot.json
  hostnames: []
hyperwatch:
  family: PerplexityBot
  identity: Perplexity
last_checked: 2026-10-15
---

# PerplexityBot

## Description

PerplexityBot is the crawler of Perplexity, an AI answer engine. Perplexity says it is "designed to
surface and link websites in search results on Perplexity" and "is not used to crawl content for
AI foundation models".

## Behavior

Perplexity documents that PerplexityBot follows `robots.txt` and that changes can take up to
24 hours to apply. Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; PerplexityBot/1.0; +https://perplexity.ai/perplexitybot)
```

This matches the documented string.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Perplexity by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exch` (5%) |
| `accept-language` | `en-US,en;q=0.9` (5%) |
| `cache-control` | `no-cache` (5%) |
| `from` | `crawler-support@perplexity.ai` (95%) |
| `upgrade-insecure-requests` | `1` (5%) |

## Blocking with robots.txt

```
User-agent: PerplexityBot
Disallow: /
```

The `PerplexityBot` and `Perplexity-User` settings are independent. Perplexity-User, which fetches
pages on behalf of users, "generally ignores robots.txt rules".

## IP ranges and verification

Perplexity publishes the addresses at https://www.perplexity.com/perplexitybot.json, which
redirects to https://www.perplexity.ai/perplexitybot.json. The format is an object with
`creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` objects. On the check date it held
8 IPv4 prefixes, with `creationTime` 2025-02-07. Perplexity recommends matching both the user agent
and the source address, and refreshing rules from the list regularly. No reverse DNS names or ASN
are documented. The addresses are in AWS, so an `amazonaws.com` hostname proves nothing.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Reverse DNS hostnames:

- `*.compute-1.amazonaws.com` (forward-confirmed, addresses in the published ranges)

## Hyperwatch

`@hyperwatch/useragent` returns the family `PerplexityBot`. `src/modules/identity.js` sets the
identity `Perplexity` when the address is in `src/data/perplexitybot-ips.json` (8 ranges, from the
published list).

## Misc

- Perplexity-User fetches pages when a user asks a question. User agent:
  `Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Perplexity-User/1.0; +https://perplexity.ai/perplexity-user)`.
  Its list is https://www.perplexity.com/perplexity-user.json (4 IPv4 prefixes on the check date).
  It is not used for crawling or training, and generally ignores `robots.txt`. Hyperwatch parses it
  as the family `Perplexity-User` and sets the identity `Perplexity` when the address is in
  `src/data/perplexity-user-ips.json`.
- On 2025-08-04 Cloudflare reported that, when its declared crawlers were blocked, Perplexity used
  undeclared crawlers with a generic Chrome on macOS user agent and unlisted addresses. Cloudflare
  removed Perplexity from its verified bots.

## Sources

- https://docs.perplexity.ai/guides/bots (checked 2026-10-15)
- https://www.perplexity.com/perplexitybot.json (checked 2026-10-15)
- https://www.perplexity.com/perplexity-user.json (checked 2026-10-15)
- https://blog.cloudflare.com/perplexity-is-using-stealth-undeclared-crawlers-to-evade-website-no-crawl-directives/ (checked 2026-10-15)
