---
name: CCBot
operator: Common Crawl Foundation
website: https://commoncrawl.org
documentation: https://commoncrawl.org/ccbot
category: archive
robots_txt_token: CCBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://index.commoncrawl.org/ccbot.json
  hostnames:
    - crawl.commoncrawl.org
hyperwatch:
  family: CCBot
  identity: Common Crawl
last_checked: 2026-10-15
---

# CCBot

## Description

CCBot is the crawler of Common Crawl, a non-profit that publishes a free, open archive of web
crawl data. The archive is used for research and is widely used to train AI models.

## Behavior

From the Common Crawl FAQ:

- CCBot is based on Apache Nutch and runs on Apache Hadoop.
- It reads `robots.txt` before fetching pages and "will periodically continue to check" for
  updates. The caching period is not documented.
- It obeys `Crawl-delay`.
- By default it waits a few seconds between requests to the same site, and backs off on HTTP 429
  and 5xx responses.
- It honors `nofollow` on links.
- It does not execute JavaScript and does not use cookies.

## User agents

Exact strings, one per line:

```
CCBot/2.0 (https://commoncrawl.org/faq/)
```

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: CCBot
Disallow: /
```

`Crawl-delay` is supported (the FAQ example `Crawl-delay: 2` limits CCBot to one request every two
seconds). Common Crawl also mentions an opt-out registry. Common Crawl warns that other crawlers
falsely identify themselves as CCBot.

## IP ranges and verification

Common Crawl publishes its ranges at https://index.commoncrawl.org/ccbot.json. The format is the
same as Google's and Bing's lists: an object with `synctoken`, `creationTime`, `notes` and a
`prefixes` array of `{"ipv4Prefix": ...}` or `{"ipv6Prefix": ...}` objects. On the check date it
held 5 prefixes (4 IPv4, 1 IPv6), created 2026-08-11.

CCBot runs on dedicated ranges with reverse DNS. An IPv4 address resolves to a name such as
`18-97-14-84.crawl.commoncrawl.org`, which resolves back to the same address. Reverse DNS is not
yet available for IPv6. The addresses are in AWS; an `amazonaws.com` hostname alone proves nothing.

## Hyperwatch

`@hyperwatch/useragent` returns the family `CCBot`. `src/modules/identity.js` sets the identity
`Common Crawl` when the address is in `src/data/ccbot-ips.json` (5 ranges, copied from
`ccbot.json`). It does not use reverse DNS for CCBot.

## Misc

Common Crawl data is distributed publicly, so pages it fetches can end up in many third-party
datasets.

## Sources

- https://commoncrawl.org/ccbot (checked 2026-10-15)
- https://commoncrawl.org/faq (checked 2026-10-15)
- https://index.commoncrawl.org/ccbot.json (checked 2026-10-15)
