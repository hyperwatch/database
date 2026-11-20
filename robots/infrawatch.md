---
name: Infrawatch
operator: Infrawatch Limited
website: https://infrawatch.com
documentation: https://infrawat.ch/
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: Infrawatch
last_checked: 2026-11-19
---

# Infrawatch

## Description

Infrawatch is the internet-wide scanner of Infrawatch Limited, a company registered in England and
Wales (company number 16347462, registered office in London). Its traffic reference page,
`infrawat.ch`, says Infrawatch "conducts internet measurement and security research to help improve
understanding of publicly accessible internet infrastructure". The scan data feeds Infrawatch's
commercial platform (`infrawatch.com`), which describes itself as "the intelligence layer for the
internet" and gives "220M+ internet-connected hosts a day" and "500M+ identified services a day".

## Behavior

The traffic reference page gives the scope as "public-facing hosts and services" and the activity
as "internet measurement and service identification". It says Infrawatch does not intentionally
attempt to exploit vulnerabilities, does not bypass authentication or brute-force access, does not
intentionally deny service and does not access non-public data.

Which ports and paths it requests, its rate, whether it renders JavaScript and whether it reads
`robots.txt` are not documented.

## User agents

Not documented. The traffic reference page gives no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Infrawatch names no `robots.txt` token and does not say whether it reads
`robots.txt`.

Exclusion goes by email to `opt-out@infrawat.ch`. The request should come from the network owner or
an authorised representative and include evidence of control over the network or assets, with the
IP address, CIDR range, ASN or domain, the organisation name, a contact email and any supporting
context. Requests without evidence of ownership or authority "may not be actioned". Abuse reports go
to `abuse@infrawat.ch`, with logs, timestamps and source addresses.

## IP ranges and verification

None published. Infrawatch documents no IP list, reverse DNS names or ASN.

Not documented, from checks run on 2026-11-19: the RIPE database has address ranges with netname
`INFRAWATCH`, registered to the organisation `ORG-IL948-RIPE` (Infrawatch Limited) and routed by
AS25369 (Hydra Communications), with the remark "Real time internet intelligence data infrawat.ch".
Their addresses have reverse DNS names of the form `*-*-*-*.infrawat.ch` (the IPv4 address with
dashes), and these names resolve back to the same address (forward-confirmed).

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`Infrawatch` on a forward-confirmed hostname matching `*-*-*-*.infrawat.ch`, whatever the user
agent.

## Misc

The company's home page is `infrawatch.com`; `infrawat.ch` is only the traffic reference page for
people who find the scanner in their logs.

## Sources

- https://infrawat.ch/ (checked 2026-11-19)
- https://infrawatch.com/ (checked 2026-11-19)
- RIPE RDAP (`https://rdap.db.ripe.net/`), records of the `INFRAWATCH` ranges and of `ORG-IL948-RIPE` (checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
