---
name: AliyunSecBot
operator: Alibaba Cloud (by its user agent's contact address; not confirmed by Alibaba documentation)
website: https://www.alibabacloud.com
documentation: null
category: other
robots_txt_token: AliyunSecBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: AliyunSecBot
  identity: AliyunSecBot
last_checked: 2026-10-15
---

# AliyunSecBot

## Description

AliyunSecBot is a user agent whose name points to Aliyun, the Chinese name of Alibaba Cloud, and
whose contact address is at `service.alibaba.com`. No Alibaba Cloud page describing it was found,
in English or Chinese. Third-party bot directories describe it as a security scanner of Alibaba's
cloud security services, without citing an Alibaba source.

## Behavior

Not documented by Alibaba. According to Known Agents, it checks sites for vulnerabilities, threats
and compliance issues and probes login pages, admin panels and API endpoints. Crawl rate,
`Crawl-delay` support, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Exact strings, one per line:

```
AliyunSecBot/Aliyun (AliyunSecBot@service.alibaba.com)
AliyunSecBot/Aliyun AliyunSecBot@service.alibaba.com
```

Alibaba does not publish its user agent. The first string is given by several third-party
directories, the second by the crawler-user-agents list.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: AliyunSecBot
Disallow: /
```

This uses the name in the user agent. Whether the robot reads `robots.txt` is not documented
(Known Agents expects it to; this is not an operator statement).

## IP ranges and verification

None published. No IP list, reverse DNS names or ASN are documented. Known Agents also says
AliyunSecBot "does not publish a verification method".

## Hyperwatch

`@hyperwatch/useragent` returns the family `AliyunSecBot` for both strings.
`src/modules/identity.js` sets the identity `AliyunSecBot` when the address is in the inline
range `8.217.0.0/16`. Alibaba documents no such range for this robot. In APNIC whois, that range
is `AlibabaCloud_HK` (Aliyun Computing Co.LTD), and RADb has a route object for `8.208.0.0/12`
with origin AS45102. It is an Alibaba Cloud Hong Kong range, which any Alibaba Cloud customer renting a server there can use.

## Misc

Nothing documented.

## Sources

- https://www.alibabacloud.com/help/en/security-center/ (no mention of AliyunSecBot, checked 2026-10-15)
- https://knownagents.com/agents/aliyunsecbot (checked 2026-10-15)
- https://raw.githubusercontent.com/monperrus/crawler-user-agents/master/crawler-user-agents.json (checked 2026-10-15)
- `whois 8.217.0.0` and `whois -h whois.radb.net 8.217.0.0/16` (checked 2026-10-15)
