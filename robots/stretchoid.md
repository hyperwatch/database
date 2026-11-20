---
name: Stretchoid
operator: Microsoft Corporation (by the domain's whois record; not stated on stretchoid.com)
website: https://stretchoid.com
documentation: https://stretchoid.com/
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: Stretchoid
last_checked: 2026-11-19
---

# Stretchoid

## Description

Stretchoid's site is a single opt-out page. It describes Stretchoid as "a platform that helps
identify an organization's online services", whose activity is sometimes flagged as malicious by
firewalls and which it calls "completely harmless". The page names no company, purpose beyond
that sentence, or contact address.

Not documented, from a whois lookup on 2026-11-19: the domain `stretchoid.com` (created 2016-05-09,
registrar MarkMonitor) is registered to the organization "Microsoft Corporation".

## Behavior

Not documented: the page says only that Stretchoid scans infrastructure. Ports, paths, rate,
JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. The page gives no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Stretchoid names no `robots.txt` token and does not say whether it reads
`robots.txt`. `https://stretchoid.com/robots.txt` returned 404 on 2026-11-19.

To stop being scanned, submit the opt-out form on https://stretchoid.com/ with a name, an email
address, a CIDR block and optional additional information.

## IP ranges and verification

None published. Stretchoid documents no IP list, reverse DNS names or ASN.

Not documented, from a DNS check on 2026-11-19: scanner addresses had reverse DNS names of the form
`azpd*.stretchoid.com` (`azpd` followed by 8 lowercase letters and digits), and these names resolve
back to the same address (forward-confirmed). The addresses were in AS8075 (Microsoft), the Azure
network: any Azure customer can use them, but only the owner of `stretchoid.com` can make them
resolve to its names.

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`Stretchoid` on a forward-confirmed hostname matching `azpd*.stretchoid.com`, whatever the user
agent.

## Misc

Nothing documented.

## Sources

- https://stretchoid.com/ (checked 2026-11-19)
- https://stretchoid.com/robots.txt (checked 2026-11-19: 404)
- `whois stretchoid.com` (checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
