---
name: ev-crawler
operator: Headline
website: https://headline.com
documentation: https://headline.com/web-crawler/
category: other
robots_txt_token: ev-crawler
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: ev-crawler
  identity: Headline
last_checked: 2026-10-15
---

# ev-crawler

## Description

ev-crawler is the crawler of Headline, a venture capital firm. Headline says it visits websites
"every so often" for publicly available information such as home page content, job postings, team
pages and location references, because it is "constantly searching the world for interesting
companies".

## Behavior

Not documented beyond the description above.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ev-crawler/1.0; +https://headline.com/web-crawler)
```

Headline's page does not give the user agent. This string comes from Known Agents. The URL
`https://headline.com/legal/crawler` redirects to the same page.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: ev-crawler
Disallow: /
```

The token is taken from the user agent. Headline does not mention `robots.txt`. It asks site owners
who would prefer not to be crawled to write to the address on its page.

## IP ranges and verification

None published. No hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `ev-crawler`. Hyperwatch sets the
identity `Headline` when the reverse DNS name ends with `.headline.com`. The hostname is not
confirmed by a forward lookup, so whoever controls an address's reverse DNS can set it. Headline
does not document this hostname.

## Misc

Nothing else documented.

## Sources

- https://headline.com/web-crawler/ (checked 2026-10-15, reached from https://headline.com/legal/crawler)
- https://knownagents.com/agents/ev-crawler (checked 2026-10-15)
