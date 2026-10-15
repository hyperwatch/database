---
name: Perplexity-User
operator: Perplexity AI
website: https://www.perplexity.ai
documentation: https://docs.perplexity.ai/docs/resources/perplexity-crawlers
category: ai-assistant
robots_txt_token: Perplexity-User
respects_robots_txt: no
verification:
  method: ip-list
  ip_list: https://www.perplexity.com/perplexity-user.json
  hostnames: []
hyperwatch:
  family: Perplexity-User
  identity: Perplexity
last_checked: 2026-10-15
---

# Perplexity-User

## Description

Perplexity-User fetches pages for users of Perplexity, an AI answer engine. Perplexity says that
"when users ask Perplexity a question, it might visit a web page to help provide an accurate answer
and include a link to the page in its response". It "is not used for web crawling or to collect
content for training AI foundation models".

## Behavior

Perplexity says that "since a user requested the fetch, this fetcher generally ignores robots.txt
rules". Request rate, caching and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko; compatible; Perplexity-User/1.0; +https://perplexity.ai/perplexity-user)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Perplexity-User
Disallow: /
```

Perplexity lists the token, says each setting works independently and that changes may take up to
24 hours, but also that Perplexity-User generally ignores `robots.txt`. Blocking it reliably needs
a server or firewall rule. Blocking PerplexityBot does not affect it.

## IP ranges and verification

Perplexity publishes the addresses at https://www.perplexity.com/perplexity-user.json, which
redirects to https://www.perplexity.ai/perplexity-user.json. The format is an object with
`creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` objects. On 2026-10-15 it held 4
IPv4 prefixes, with `creationTime` 2025-10-17. Perplexity recommends matching both the user agent
and the source address, and refreshing rules from the list regularly. No reverse DNS hostname or
ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Perplexity-User`. In `src/modules/identity.js`,
Hyperwatch sets the identity `Perplexity` when the address is in
`src/data/perplexity-user-ips.json`, written by `node scripts/fetch-perplexity-ips.js` from the
published list. On 2026-10-15 it held the same 4 prefixes as the published list.

## Misc

- PerplexityBot, Perplexity's crawler for its search results, has its own file and list.
- On 2025-08-04 Cloudflare reported that Perplexity used undeclared crawlers with a generic browser
  user agent when its declared crawlers were blocked (see the PerplexityBot file).

## Sources

- https://docs.perplexity.ai/guides/bots (checked 2026-10-15, redirects to https://docs.perplexity.ai/docs/resources/perplexity-crawlers)
- https://www.perplexity.com/perplexity-user.json (checked 2026-10-15)
