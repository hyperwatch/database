---
name: ForestEngine
operator: F.O.R.E.S.T. L.L.C (Forest)
website: https://forest.info
documentation: https://forestengine.net/
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://forestengine.net/#identify
  hostnames: []
hyperwatch:
  family: ForestEngine
  identity: Forest
last_checked: 2026-11-19
---

# ForestEngine

## Description

ForestEngine is "the scanning infrastructure behind Forest", an internet intelligence search
platform run by F.O.R.E.S.T. L.L.C, a company registered in Dubai, United Arab Emirates. Forest
says it "continuously scans, indexes, and maps the global internet": TLS certificates, domains, open
ports and services, and HTTP headers, searchable through a web interface and an API.

## Behavior

ForestEngine checks a fixed list of ports and records what answers. On a web port it requests the
home page; if the page names a site icon it requests that icon, otherwise `/favicon.ico`, "the only
path we guess". It does not follow links, walk a site or try lists of paths. It collects TLS
certificates, response headers, service banners and the page a web port returns. It does not brute
force, never sends an exploit, and does not read, change or delete stored data. On a few database
and message ports, the protocol's opening packet carries the name "default" with no password. DNS
data is collected through public resolvers, never by zone transfer.

Rate (beyond "a small number of low-rate connections"), JavaScript rendering and `robots.txt`
handling are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ForestEngine/1.0; +https://forestengine.net/)
```

ForestEngine says it adds to its list of user agents rather than replacing it. Its probes on other
ports carry no identifier.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: ForestEngine names no `robots.txt` token and does not mention `robots.txt`.

It suggests blocking its ranges or opting out. The opt-out is a form on its page, for network owners
and operators, covering up to 25 single addresses, domains or hostnames per request (not CIDR ranges
or ASNs). Control is proved with a temporary DNS record: a TXT record for a domain or hostname, a
reverse DNS (PTR) value for an address. An opt-out lasts 12 months and is renewed with a new record.

## IP ranges and verification

ForestEngine publishes its ranges in the "How to identify us" section of its page, as HTML, not a
machine-readable file. On 2026-11-19 it listed one IPv4 prefix, `151.245.151.0/24`, with no
generation date. It says it adds to this list rather than replacing it, and that for probes on ports
other than HTTP "the address list is the only signal". No reverse DNS names or ASN are documented.

From the RIPE database (checked 2026-11-19): `151.245.151.0/24` carries a certificate named
`FOREST-LLC-BYOIP-151-245-151-0` (a bring-your-own-IP proof); it is announced by AS393406
(DigitalOcean).

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 returns the family `ForestEngine`.

In Hyperwatch `main` (after 5.7.0, not released yet), `src/modules/identity.js` sets the identity
`Forest` on family `ForestEngine` from an address in the inline range `151.245.151.0/24`, its only
range.

## Misc

The opt-out page notes that, for an address opt-out, Forest has "not built the delete path for
address-keyed records yet". Personal data requests go through the Forest contact form
(https://forest.info/contact).

## Sources

- https://forestengine.net/ (checked 2026-11-19)
- https://forest.info/ and https://forest.info/about (checked 2026-11-19)
- RIPE RDAP (`https://rdap.org/ip/`), the `151.245.151.0/24` record (checked 2026-11-19)
