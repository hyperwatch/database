---
name: CensysInspect
operator: Censys, Inc.
website: https://censys.com
documentation: https://docs.censys.com/docs/opt-out-of-data-collection
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://docs.censys.com/docs/opt-out-of-data-collection
  hostnames: []
hyperwatch:
  family: CensysInspect
  identity: Censys
last_checked: 2026-11-19
---

# CensysInspect

## Description

CensysInspect is the user agent of the HTTP scans of Censys, an internet security platform that
"helps organizations discover, monitor, and secure their devices on the Internet". Censys says it
regularly probes every public IP address and website, then curates and enriches the data for
enterprises (attack surface), CERT groups (alerting operators of vulnerable systems) and researchers.
Censys started as a research project at the University of Michigan, by the team that created ZMap,
and has since spun out into an independent company.

## Behavior

Censys makes "small, harmless connection attempts to every IPv4 address worldwide" and, when a
server accepts connections, completes a protocol handshake (an HTTP request, for instance). It scans
the whole IPv4 space on all 65,535 ports, more than 100 popular ports continually, the address
ranges of AWS, Azure and GCP at least once a day, and IPv6 addresses found through redirects and DNS.
Known services whose last observation is older than 24 hours are rescanned.

On ports running HTTP(S), Censys requests the root page (`/`), follows local redirects, and makes
follow-up requests to identify and classify HTTP applications. It says it never attempts to bypass
authentication or technical barriers, exploit security problems or access non-public services.

JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; CensysInspect/1.1; +https://about.censys.io/)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Censys names no `robots.txt` token and does not say whether it reads `robots.txt`.

Censys's opt-out is network-level: drop traffic from its published scanning ranges, or filter on
its user agent. Blocking stops new indexing but does not remove historical data; host services
usually leave Censys Search 24 to 48 hours after their last observation. To be excluded from
scans, the WHOIS contact of the address block or domain emails `censys-abuse@censys.com`, or the
requester provides documentation from the domain registrar and the ISP confirming ownership. Censys
does not exclude addresses dedicated to cloud hosting.

## IP ranges and verification

Censys publishes the ranges it scans from in the "Allowlist or blocklist scans" section of its
opt-out page, https://docs.censys.com/docs/opt-out-of-data-collection: a plain-text block inside the
HTML page (no machine-readable file), with 16 IPv4 prefixes (all `/24`), 4 IPv6 prefixes (`/80` and
`/112`) and 3 ASNs (AS398722, AS398705, AS398324). The list carries no generation date; the page's
Markdown version (`.md` suffix) gives `updatedAt: 2026-10-28T14:32:44.000Z`, on 2026-11-19.

`about.censys.io` adds that Censys "sometimes make[s] follow-up connections from other machines at
dynamic IP addresses", outside those ranges.

No reverse DNS names are documented.

Not documented, from a DNS check on 2026-11-19: addresses in the published ranges have reverse DNS
names of the form `*.*.*.*.censys-scanner.com` (the IPv4 address reversed), and these names
resolve back to the same address (forward-confirmed). The addresses checked were in AS398324
(Censys, Inc.).

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 parses the string above as family `CensysInspect`.

In Hyperwatch `main` (after 5.7.0, not released yet), `src/modules/identity.js` sets the identity
`Censys` on family `CensysInspect` from an address in Censys's published ranges (`censys-ips.json`,
copied by hand from its opt-out page). The "hostname only" fallback also sets `Censys` on a
forward-confirmed hostname matching `*.*.*.*.censys-scanner.com`, whatever the user agent.

## Misc

Censys says its scans can be checked as benign on GreyNoise. It uses IPinfo for geolocation and
RouteViews for routing data, and the ZMap Project, which it maintains, remains an independent
open-source project.

## Sources

- https://docs.censys.com/docs/opt-out-of-data-collection (and its `.md` version, checked 2026-11-19)
- https://docs.censys.com/docs/internet-scanning (checked 2026-11-19)
- https://docs.censys.com/docs/scanning-faq (checked 2026-11-19)
- https://about.censys.io/ (checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
