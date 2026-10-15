---
name: 360Spider
operator: 360 Search (Qihoo 360)
website: https://www.so.com
documentation: https://www.so.com/help/spider_ip.html
category: search-engine
robots_txt_token: 360Spider
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: http://beijing2.xstore.qihu.com/tender/360%E8%9C%98%E8%9B%9BIP%E5%88%97%E8%A1%A8.pdf
  hostnames: []
hyperwatch:
  family: 360Spider
  identity: 360Spider
last_checked: 2026-10-15
---

# 360Spider

## Description

360Spider is the web search crawler of 360 Search (so.com), the Chinese search engine of Qihoo 360.

## Behavior

360 Search supports the `User-agent`, `Allow` and `Disallow` directives, and adds its own
`Indexpage` directive: it names pages that change often, so the crawler visits them more. Wildcards
`*` and `$` are allowed in it.

Crawl rate, `Crawl-delay` support, JavaScript rendering and how often `robots.txt` is re-read are
not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/140.0.0.0 Safari/537.36 Edg/140.0.0.0; 360Spider
```

360 Search says every crawler request carries the `360Spider` token.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: 360Spider
Disallow: /
```

The other 360 Search tokens are `360Spider-Image` (image search) and `360Spider-Video` (video search).

## IP ranges and verification

360 Search says reverse DNS (`nslookup`) does not work for its crawler and the published addresses
should be used instead. Its page lists six networks as wildcards: `42.236.10.*`, `42.236.12.*`,
`42.236.17.*`, `42.236.101.*`, `180.153.236.*` and `180.163.220.*`.

The full list is a PDF at
http://beijing2.xstore.qihu.com/tender/360%E8%9C%98%E8%9B%9BIP%E5%88%97%E8%A1%A8.pdf, one IPv4
address per line. On 2026-10-15 it held 2,183 addresses in 24 `/24` networks. The list itself has no
date; the PDF's metadata gives 2025-11-04. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `360Spider`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `360Spider` when the address is in the published
list `src/data/360spider-ips.json`, the 2,183 addresses of 360's PDF copied by hand. Because the copy
is manual, it is not refreshed when 360 updates the PDF.

## Misc

Nothing else documented.

## Sources

- https://www.so.com/help/help_3_2.html (checked 2026-10-15)
- https://www.so.com/help/spider_ip.html (checked 2026-10-15)
- http://beijing2.xstore.qihu.com/tender/360%E8%9C%98%E8%9B%9BIP%E5%88%97%E8%A1%A8.pdf (checked 2026-10-15)
