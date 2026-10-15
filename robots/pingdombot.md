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
last_checked: 2026-10-15
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

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

No token is documented, and Pingdom does not say whether its checks read `robots.txt`.

## IP ranges and verification

Pingdom publishes its probe addresses in three formats, linked from the documentation page:

- https://my.pingdom.com/probes/ipv4: plain text, one address per line. 149 addresses on
  2026-10-15.
- https://my.pingdom.com/probes/ipv6: plain text, one address per line. 57 addresses on
  2026-10-15.
- https://my.pingdom.com/probes/feed: RSS, one item per probe with its address, hostname, country,
  city, region and state. 149 items on 2026-10-15; its `lastBuildDate` is the time of the request.

The feed's hostnames are not a documented verification method. On 2026-10-15, 73 were under
`pingdom.com`, 50 under `cloud.solarwinds.com`, and 26 probes had their address in place of a
hostname. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `PingdomBot` for the three forms above.
`src/modules/identity.js` sets the identity `Pingdom` when the reverse DNS hostname ends with
`.pingdom.com`.

Where it falls short:

- it reads the unconfirmed hostname, not the forward-confirmed one;
- reverse DNS is not a method Pingdom documents;
- probes named under `cloud.solarwinds.com` or without a name in the feed do not pass;
- Hyperwatch does not use the published lists.

## Misc

- Pingdom sends webhooks from `webhook.pingdom.com` (documentation page above).

## Sources

- https://documentation.solarwinds.com/en/success_center/pingdom/content/topics/pingdom-probe-servers-ip-addresses.htm (checked 2026-10-15)
- https://documentation.solarwinds.com/en/success_center/pingdom/content/topics/google-analytics-and-pingdom.htm (checked 2026-10-15)
- https://my.pingdom.com/probes/ipv4 (checked 2026-10-15)
- https://my.pingdom.com/probes/ipv6 (checked 2026-10-15)
- https://my.pingdom.com/probes/feed (checked 2026-10-15)
