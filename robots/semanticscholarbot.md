---
name: SemanticScholarBot
operator: Allen Institute for AI (Ai2)
website: https://www.semanticscholar.org
documentation: https://www.semanticscholar.org/crawler
category: research
robots_txt_token: SemanticScholarBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: SemanticScholarBot
  identity: null
last_checked: 2026-10-15
---

# SemanticScholarBot

## Description

SemanticScholarBot is the crawler of Semantic Scholar, an academic search engine run by the Allen
Institute for AI (Ai2). It crawls certain domains to find academic PDFs, which are then served on
semanticscholar.org so researchers can find related work.

## Behavior

The operator page only says what the robot looks for (academic PDFs) and which user agent it
sends. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` handling are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible) SemanticScholarBot (+https://www.semanticscholar.org/crawler)
```

The operator says the robot always sends this string when looking for documents, and that it can
be used to filter or reject its traffic.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SemanticScholarBot
Disallow: /
```

The token is taken from the user agent. The operator does not say whether the robot obeys
`robots.txt`. It suggests filtering by user agent instead.

## IP ranges and verification

None published. No IP list, reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS16509 Amazon.com, Inc.: `35.160.27.0/24`

Reverse DNS hostnames:

- `*.us-west-2.compute.amazonaws.com` (forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `SemanticScholarBot`. Hyperwatch has
no identity for it, since there is no way to verify it.

## Misc

Ai2 runs other robots, such as AI2Bot, which are not covered here.

## Sources

- https://www.semanticscholar.org/crawler (checked 2026-10-15)
