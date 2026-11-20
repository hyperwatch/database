---
name: CriminalIP
operator: AI SPERA (Criminal IP)
website: https://www.criminalip.io
documentation: https://security.criminalip.io/
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: reverse-dns
  ip_list: null
  hostnames: ["security.criminalip.io"]
hyperwatch:
  family: CriminalIP
  identity: null
last_checked: 2026-11-19
---

# CriminalIP

## Description

Criminal IP is a cyber threat intelligence search engine operated by AI SPERA. Its "About This Scan"
page says its scanners connect to networks to check whether services are listening, and that "this
scan data powers Criminal IP's threat intelligence products, which security teams use to find their
own exposed assets and track adversary infrastructure".

## Behavior

The page describes a scan as "a single, lightweight request to check whether a service was
listening on a given port", and says Criminal IP does not attempt logins, run exploits or use
vulnerability-scanning tools. The RIPE remark on its address range (see below) adds that it "only
reads the response data from basic port requests" and that its scanning "does not target specific
IP addresses".

Paths requested, rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; CriminalIP/1.0; +https://security.criminalip.io/)
```

The page says HTTP scans use this user agent.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Criminal IP names no `robots.txt` token and does not say whether it reads
`robots.txt`.

To opt out, email `request@aispera.com` with the IP addresses or CIDR ranges to exclude and a
contact for verification. The RIPE remark says AI SPERA "will permanently whitelist your IP address
upon request".

## IP ranges and verification

No IP list is published. The page gives three checks: the reverse DNS of the address resolves to
`security.criminalip.io`; WHOIS or RDAP on the address shows an AI SPERA organisation remark; HTTP
scans use the user agent above.

The reverse DNS check cannot be forward-confirmed. On 2026-11-19, `security.criminalip.io` resolved
only to Cloudflare addresses (it serves the "About This Scan" page), and `security.criminalip.com`,
which redirects to it, resolved to a single address of the web server. A scanning address whose
reverse DNS gives either name is not among the addresses the name resolves to.

From the RIPE database (checked 2026-11-19): AI SPERA (`ORG-AS965-RIPE`) is registrant of a range
with netname `AISPERA` and a remark headed "Criminal IP Collector AiSpera", routed by
AS202425 (IP Volume inc). It is the remark quoted above. No ASN of AI SPERA's own is documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 returns the family `CriminalIP`.

Not identified by Hyperwatch, and Criminal IP cannot be verified with what it documents: the
documented reverse DNS name does not resolve back to the scanning addresses, Hyperwatch does not
read WHOIS or RDAP, and a user agent is not proof.

## Misc

Nothing else documented.

## Sources

- https://security.criminalip.io/ (redirect from https://security.criminalip.com/, checked 2026-11-19)
- https://www.criminalip.io/ (checked 2026-11-19)
- RIPE RDAP (`https://rdap.db.ripe.net/`), the `AISPERA` range and `ORG-AS965-RIPE` (checked 2026-11-19)
- Forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
