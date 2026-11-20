---
name: internet-census.org
operator: Internet Census Group (led by BitSight Technologies, Inc.)
website: https://www.internet-census.org
documentation: https://www.internet-census.org/home.html
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: reverse-dns
  ip_list: null
  hostnames: [".internet-census.org"]
hyperwatch:
  family: null
  identity: Internet Census
last_checked: 2026-11-19
---

# internet-census.org

## Description

The Internet Census Group scans the internet to "analyze trends and benchmark security performance
across a broad range of industries". Its site says the group "is led by BitSight Technologies, Inc."
and that the data is used to improve BitSight's Security Ratings service and to evaluate the
security performance of an entity or a country. High-impact vulnerability information is shared
with authorities such as national CSIRTs, and some of it with the scanned entities on request.

## Behavior

The group makes connection attempts to publicly accessible systems and, where a system responds,
attempts a protocol handshake. It says it only collects what any client connecting to that address
and port would see, and never attempts to change device configurations. It collects installed
versions of network-exposed services, applications and libraries (WordPress, Apache, PHP…), metadata
(open ports, running services, banners, TLS certificates, enabled features) and vulnerability
information when a service behaves in a way that strongly correlates with a specific vulnerability.
On an unauthenticated database it collects only a sample of the information schema, not the tables'
contents, and stores possibly sensitive data in hashed form.

Paths requested, rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. The site gives no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: the group names no `robots.txt` token and does not say whether it reads
`robots.txt`.

Its opt-out is a list of IP addresses excluded from scanning: send the addresses to
`optout@internet-census.org`. An approved opt-out lasts six months and must be renewed at the end of
each period; the requester agrees to report changes of addresses or networks.

## IP ranges and verification

No IP list is published. The group documents reverse DNS with forward confirmation: the reverse DNS
name of a scanning address must belong to the `internet-census.org` domain, and a lookup of that
name must return the initial address. Its example name is `sh-chi-us-gp1-wk101.internet-census.org`.
No ASN is documented.

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`Internet Census` on a forward-confirmed hostname matching `*.internet-census.org`, whatever the
user agent.

## Misc

The site's footer reads "© 2024 Internet Census Group".

## Sources

- https://www.internet-census.org/home.html (redirect from https://internet-census.org/, checked 2026-11-19)
- https://www.internet-census.org/about-us.html (checked 2026-11-19)
- https://www.internet-census.org/privacy-policy.html (checked 2026-11-19)
