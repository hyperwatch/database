---
name: academyforinternetresearch.org
operator: Unknown
website: https://academyforinternetresearch.org
documentation: https://web.archive.org/web/20250711090029/https://securityscan.academyforinternetresearch.org/
category: unknown
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: null
last_checked: 2026-11-19
---

# academyforinternetresearch.org

## Description

The Academy For Internet Research described itself as "a group of Security Researchers interested in
making the internet a safer place", whose "security scans help to the advance academic work and the
study of the internet". It said the data is used "towards research and other programs intended on
making the Internet safer". Its page names no organisation, institution or person, and neither do
the domain's registration data nor its certificates (see [Misc](#misc)): the operator is unknown.

That description comes from archived copies of `https://securityscan.academyforinternetresearch.org/`
(the latest dated 2025-07-11). On 2026-11-19 that address served an unrelated online gambling page,
and `https://academyforinternetresearch.org/` only the text "academyforinternetresearch.org".

## Behavior

The archived page said the scans are "benign in nature" and "passive in nature, intended to collect
information": they "will never attempt to log in to any service, read any database or obtain
authenticate access". It said they were "scanning 1400 ports across a number of protocols refreshed
bi-weekly", and are "only interested in collecting information about new services, and refreshing
and aging out old information".

Paths requested, rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. The archived page gives no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: no `robots.txt` token is named.

To opt out, the archived page said to email `abuse` at `academyforinternetresearch.org` or at
`deptofinternetservices.org`. On 2026-11-19, `deptofinternetservices.org` was not registered.

## IP ranges and verification

None published: the archived page documents no IP list, reverse DNS names or ASN.

Not documented, from a DNS check on 2026-11-19: scanning addresses in AS63949 (Akamai Connected
Cloud, Linode) have reverse DNS names `prod<NN>client01.academyforinternetresearch.org`, but these
names don't exist in the domain's DNS (its own nameservers, at Cloudflare, answer that the name does
not exist), so they cannot be forward-confirmed. Whoever controls an address's reverse DNS can set
such a name.

## Hyperwatch

No user agent is documented, so no agent family can be given.

Not identified by Hyperwatch, and it can't be verified: no address list is published, and the
reverse DNS names are not forward-confirmed, so they prove nothing about who sends the requests.

## Misc

According to its registration data (RDAP), `academyforinternetresearch.org` was registered on
2021-10-03 through NameCheap, without a named registrant. Certificate Transparency logs show
certificates for `securityscan.academyforinternetresearch.org` since 2022-09.

## Sources

- https://web.archive.org/web/20231222143050/https://securityscan.academyforinternetresearch.org/ (archived copy, checked 2026-11-19)
- https://web.archive.org/web/20250711090029/https://securityscan.academyforinternetresearch.org/ (archived copy, checked 2026-11-19)
- https://securityscan.academyforinternetresearch.org/ (checked 2026-11-19)
- https://academyforinternetresearch.org/ (checked 2026-11-19)
- https://rdap.org/domain/academyforinternetresearch.org and https://rdap.org/domain/deptofinternetservices.org (checked 2026-11-19)
- https://crt.sh/?q=%25.academyforinternetresearch.org (checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8, and through the domain's nameserver `liz.ns.cloudflare.com` (checked 2026-11-19)
