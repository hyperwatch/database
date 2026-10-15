---
name: SentryUptimeBot
operator: Sentry
website: https://sentry.io
documentation: https://docs.sentry.io/product/monitors-and-alerts/monitors/uptime-monitoring/troubleshooting/
category: monitoring
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://sentry.io/api/0/uptime-ips/
  hostnames: []
hyperwatch:
  family: SentryUptimeBot
  identity: Sentry
last_checked: 2026-10-15
---

# SentryUptimeBot

## Description

SentryUptimeBot makes the requests of Sentry's uptime monitoring, which checks that customers'
URLs respond.

## Behavior

Request method, headers, redirects, timeouts and `robots.txt` handling are not documented on the
pages checked.

## User agents

Exact strings, one per line:

```
SentryUptimeBot/1.0 (+https://docs.sentry.io/product/monitors-and-alerts/monitors/uptime-monitoring/)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

No token is documented, and Sentry does not say whether its uptime checks read `robots.txt`.

## IP ranges and verification

Sentry publishes the addresses of its uptime checks on its IP ranges page and at
https://sentry.io/api/0/uptime-ips/ (plain text, one address per line, no date). On 2026-10-15 both
held the same 12 IPv4 addresses.

Sentry recommends checking the user agent rather than the address, because its addresses "can
change without notice". No reverse DNS hostname or ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SentryUptimeBot`. `src/modules/identity.js` sets the
identity `Sentry` when the reverse DNS hostname ends with `.googleusercontent.com`. This is a cloud
hostname: any Google Cloud customer passes it. The suffix is not documented by Sentry, and
Hyperwatch does not use the published list.

## Misc

Nothing else documented.

## Sources

- https://docs.sentry.io/product/monitors-and-alerts/monitors/uptime-monitoring/troubleshooting/ (checked 2026-10-15)
- https://docs.sentry.io/security-legal-pii/security/ip-ranges/ (checked 2026-10-15)
- https://sentry.io/api/0/uptime-ips/ (checked 2026-10-15)
