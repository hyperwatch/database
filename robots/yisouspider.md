---
name: YisouSpider
operator: Shenma (by Hyperwatch's hostname rule; not confirmed by Shenma documentation)
website: https://m.sm.cn
documentation: null
category: unknown
robots_txt_token: YisouSpider
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: Shenma
last_checked: 2026-10-15
---

# YisouSpider

## Description

YisouSpider is a crawler whose operator is not documented. Hyperwatch attributes it to Shenma
(sm.cn), the Chinese search engine of Alibaba Group, from `.crawl.sm.cn` hostnames; Known Agents
names the operator only as "Yisou". Shenma's webmaster platform (zhanzhang.sm.cn) was checked: its
help page and terms of service do not mention YisouSpider or describe a crawler. The terms list
Shenma Search among Alibaba Group's platforms.

## Behavior

Not documented. Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` handling
are unknown. The Shenma terms of service say Shenma Search cannot serve sites that block crawlers.

## User agents

No full string was found on Shenma's pages or in the third-party sources fetched. Known Agents gives
only the token `YisouSpider`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented by Shenma. According to Known Agents:

```
User-agent: YisouSpider
Disallow: /
```

## IP ranges and verification

None published. Shenma's pages give no IP list, reverse DNS hostnames or ASN.

## Hyperwatch

No full user agent string was available to parse, so the agent family is not recorded here.
`src/modules/identity.js` sets the identity `Shenma` for the family `YisouSpider` when the
unconfirmed hostname ends with `.crawl.sm.cn`. A fallback also sets `Shenma` for any request,
whatever its user agent, with an unconfirmed hostname ending in `.crawl.sm.cn`. Shenma does not
document that suffix, and neither check is forward-confirmed.

## Misc

Nothing else documented.

## Sources

- https://zhanzhang.sm.cn/ (checked 2026-10-15)
- https://zhanzhang.sm.cn/open/help (checked 2026-10-15)
- https://knownagents.com/agents/yisouspider (checked 2026-10-15)
