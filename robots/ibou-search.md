---
name: ibou-search
operator: ibou
website: https://www.ibou.com
documentation: https://www.ibou.com/crawlers.html
category: search-engine
robots_txt_token: ibou-search
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://www.ibou.com/ibousearch-ip-ranges.json
  hostnames:
    - ibou.io
hyperwatch:
  family: ibou-search
  identity: null
last_checked: 2026-10-15
---

# ibou-search

## Description

ibou-search is the crawler of ibou, a French search engine. It "discovers publicly accessible pages
and indexes them for our search engine". ibou states that it does not train AI models with the
data.

## Behavior

- Crawl rate: 5 seconds between two requests to the same host, and 2.5 seconds between requests to
  the same IP for the same domain. ibou gives about 0.4 requests per second per domain (about 24
  per minute) as the worst case.
- `Crawl-delay` is supported, per host.
- It follows `robots.txt`.
- JavaScript rendering is not documented. How often `robots.txt` is re-read is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ibou-search/2.0; +https://ibou.com/crawlers.html)
```

ibou documents `Mozilla/5.0 (compatible; ibou-search/2.0; +https://www.ibou.com/crawlers.html)`,
with `www.` in the URL. Its technical table gives the version as 1.0 while the user agent says 2.0.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: ibou-search
Disallow: /
```

To slow it down instead:

```
User-agent: ibou-search
Crawl-Delay: 10
```

## IP ranges and verification

- IP list: https://www.ibou.com/ibousearch-ip-ranges.json. JSON object with `creationTime` and a
  `prefixes` array whose objects carry `ipv4Prefix` and `ipv6Prefix` keys. On the check date it held
  one entry: `188.241.38.0/24` and `2a0e:6240:e000::/44`, with `creationTime` 2026-09-28. ibou says
  the list may change and should be fetched periodically.
- Reverse DNS: forward-confirmed names under `ibou.io`, for example `c40037.ibou.io`.
- ASN: not documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ibou-search`. `src/modules/identity.js` has no rule for
it, so it gets no identity, even though ibou publishes both an IP list and reverse DNS.

## Misc

- ibou's site also links to a page about `IbouBot`. The crawler page does not say how the two
  relate.
- Cloudflare classifies ibou-search as a search crawler, according to ibou.

## Sources

- https://www.ibou.com/crawlers.html (checked 2026-10-15)
- https://www.ibou.com/ibousearch-ip-ranges.json (checked 2026-10-15)
