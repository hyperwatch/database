---
name: PingdomBot
operator: SolarWinds (Pingdom)
website: https://www.pingdom.com
documentation: https://documentation.solarwinds.com/en/success_center/pingdom/content/topics/pingdom-probe-servers-ip-addresses.htm
category: monitoring
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://my.pingdom.com/probes/ipv4
  hostnames: []
hyperwatch:
  family: PingdomBot
  identity: Pingdom
last_checked: 2026-11-10
---

# PingdomBot

## Description

Pingdom is SolarWinds' website monitoring service. Its probe servers request customers' pages to
check that they are up and to measure their speed.

## Behavior

The Pingdom documentation says page speed checks and transaction checks run in a real Chrome
browser, while basic uptime checks do not trigger JavaScript-based analytics. Request rate and
`robots.txt` handling are not documented.

## User agents

The Pingdom documentation gives no full string. It says Pingdom's visits can be recognized by the
word `pingdom` in the user agent.

`@hyperwatch/useragent` recognizes three forms as Pingdom: `Pingdom.com_bot_version_<version>`,
`PingdomTMS/<version>` and `PingdomPageSpeed/<version>`. These come from the parser's rules, not from
Pingdom.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-11-10, pages, verified as Pingdom by Hyperwatch 5.4.0.

No header other than the user agent and those set on the way.

Never sent: `accept`, `accept-language`.

## Blocking with robots.txt

No token is documented, and Pingdom does not say whether its checks read `robots.txt`.

## IP ranges and verification

Pingdom publishes its probe addresses in three formats, linked from the documentation page:

- https://my.pingdom.com/probes/ipv4: plain text, one address per line. 153 addresses on
  2026-11-10 (149 on 2026-10-15).
- https://my.pingdom.com/probes/ipv6: plain text, one address per line. 57 addresses on
  2026-11-10.
- https://my.pingdom.com/probes/feed: RSS, one item per probe with its address, hostname, country,
  city, region and state. 149 items on 2026-11-10; its `lastBuildDate` is the time of the request.

The feed's hostnames are not a documented verification method. On 2026-11-10, as on 2026-10-15, 73 were under
`pingdom.com`, 50 under `cloud.solarwinds.com`, and 26 probes had their address in place of a
hostname. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `PingdomBot` for the three forms above. In Hyperwatch
`main` (after 5.4.0), `src/modules/identity.js` sets the identity `Pingdom` on a forward-confirmed
hostname matching `s*.pingdom.com` or the published list (`pingdom-ips.json`, the IPv4 and IPv6
probe lists joined: 210 addresses, the same as the published lists on 2026-11-10). The pattern is
the form of the `pingdom.com` names in the probe feed (all of them on 2026-11-10), which Pingdom
does not document as a verification method; the probes under `cloud.solarwinds.com` are covered by
the list only.

## Misc

- Pingdom sends webhooks from `webhook.pingdom.com` (documentation page above).

## Sources

- https://documentation.solarwinds.com/en/success_center/pingdom/content/topics/pingdom-probe-servers-ip-addresses.htm (checked 2026-10-15)
- https://documentation.solarwinds.com/en/success_center/pingdom/content/topics/google-analytics-and-pingdom.htm (checked 2026-10-15)
- https://my.pingdom.com/probes/ipv4 (checked 2026-11-10)
- https://my.pingdom.com/probes/ipv6 (checked 2026-11-10)
- https://my.pingdom.com/probes/feed (checked 2026-11-10)
