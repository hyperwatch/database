---
name: MojeekBot
operator: Mojeek
website: https://www.mojeek.com
documentation: https://www.mojeek.com/bot.html
category: search-engine
robots_txt_token: MojeekBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://www.mojeek.com/mojeekbot.json
  hostnames:
    - .mojeek.com
hyperwatch:
  family: MojeekBot
  identity: Mojeek
last_checked: 2026-10-15
---

# MojeekBot

## Description

MojeekBot is the web crawler of Mojeek, an independent search engine with its own index.

## Behavior

Mojeek says the robot should not request more than one page from a site in the same one-second
period, whether the request succeeds or not. It obeys the `noindex`, `nocache` and `nofollow`
robots meta tags. With `noindex` it still fetches the page but does not index it.

It does not support `Crawl-delay`. JavaScript rendering and `robots.txt` caching are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; MojeekBot/0.11; +https://www.mojeek.com/bot.html)
```

The operator page does not give a full user agent string, only the `MojeekBot` token.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: MojeekBot
Disallow: /
```

MojeekBot obeys the first record whose `User-agent` contains `MojeekBot`. If there is none, it
obeys the first `User-agent: *` record. A `Disallow` value is matched as a prefix:
`Disallow: /private` also blocks `/private/` and `/private.html`. `Crawl-delay` is not supported.

## IP ranges and verification

Mojeek recommends a forward-confirmed reverse DNS check: the address must resolve to a name in
`mojeek.com`, for example `crawl-5-102-173-71.mojeek.com`, and that name must resolve back to the
same address.

Mojeek also publishes an address list at https://www.mojeek.com/mojeekbot.json and says it may
change at any time. The file is JSON with a `creationTime` field and a `prefixes` array of objects
with an `ipv4Prefix` key. On 2026-10-15 it held 1 IPv4 prefix (`5.102.173.64/28`) and was dated
2025-05-14. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `MojeekBot`. Hyperwatch sets the
identity `Mojeek` when the verified hostname ends with `.mojeek.com`. It does not use the IP list.

## Misc

Nothing else documented.

## Sources

- https://www.mojeek.com/bot.html (checked 2026-10-15)
- https://www.mojeek.com/mojeekbot.json (checked 2026-10-15)
