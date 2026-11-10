---
name: UptimeRobot
operator: UptimeRobot
website: https://uptimerobot.com
documentation: https://help.uptimerobot.com/en/articles/11358489-what-is-the-uptimerobot-user-agent-string
category: monitoring
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://api.uptimerobot.com/meta/ips
  hostnames: []
hyperwatch:
  family: UptimeRobot
  identity: Uptime Robot
last_checked: 2026-11-10
---

# UptimeRobot

## Description

UptimeRobot is a website monitoring service. Its checkers request customers' pages at set intervals
to check that they are up.

## Behavior

Request rate, request methods, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0+(compatible; UptimeRobot/2.0; http://www.uptimerobot.com/)
```

UptimeRobot documents only this string.

## Observed HTTP headers

Based on dozens of requests seen on 2026-11-10, pages, verified as Uptime Robot by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (100%) |
| `accept-language` | `en-US,en;q=0.8` (100%) |
| `cache-control` | `no-cache` (100%) |

## Blocking with robots.txt

No token is documented, and UptimeRobot does not say whether its checks read `robots.txt`.

## IP ranges and verification

UptimeRobot publishes its checker addresses and says they can change. The locations page
(https://uptimerobot.com/help/locations/) links to:

- https://api.uptimerobot.com/meta/ips: JSON with `syncToken`, `createDate` and a `prefixes` array
  of objects with `ip_prefix` or `ipv6_prefix`, `region` and `service`. On 2026-10-15 it held 206
  prefixes (103 IPv4 `/32`, 103 IPv6 `/128`), all with `service` `checker`, dated 2026-06-24.
- https://cdn.uptimerobot.com/api/IPv4.txt (103 lines) and
  https://cdn.uptimerobot.com/api/IPv4andIPv6.txt (206 lines): plain text.
- The DNS records of `ip.uptimerobot.com`.

The locations page says new addresses replaced the old ones from July 28. No reverse DNS hostname or
ASN is documented. UptimeRobot also says checks can be recognized by their user agent.

## Hyperwatch

`@hyperwatch/useragent` returns the family `UptimeRobot`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` sets the identity `Uptime Robot` on a forward-confirmed hostname matching
`checker-*.uptimerobot.com` or the published list (`uptimerobot-ips.json`, IPv4 and IPv6). The
pattern is not documented by UptimeRobot, which documents no hostname.

## Misc

Nothing else documented.

## Sources

- https://help.uptimerobot.com/en/articles/11358489-what-is-the-uptimerobot-user-agent-string (checked 2026-10-15)
- https://help.uptimerobot.com/en/articles/11619500-do-you-have-a-list-of-ip-addresses-i-need-to-allow-for-monitoring (checked 2026-10-15)
- https://uptimerobot.com/help/locations/ (checked 2026-10-15)
- https://api.uptimerobot.com/meta/ips (checked 2026-10-15)
- https://cdn.uptimerobot.com/api/IPv4.txt (checked 2026-10-15)
- https://cdn.uptimerobot.com/api/IPv4andIPv6.txt (checked 2026-10-15)
