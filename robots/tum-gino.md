---
name: TUM GINO
operator: Technical University of Munich (Chair of Network Architectures and Services)
website: https://net.in.tum.de/projects/gino/
documentation: https://net.in.tum.de/projects/gino/scans.html
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: both
  ip_list: https://net.in.tum.de/projects/gino/scans.html
  hostnames: ["planetlab*.gino-research.net.in.tum.de", "planetlab*.net.in.tum.de"]
hyperwatch:
  family: Chrome
  identity: TUM
last_checked: 2026-11-19
---

# TUM GINO

## Description

GINO (Global INternet Observatory) is a research project of the Chair of Network Architectures and
Services at the Technical University of Munich (TUM), running since 2016-11-01. It conducts "regular
and ad-hoc Internet-wide scans" for protocols such as HTTPS (TLS over TCP and QUIC), DNS and IPv6,
which TUM describes as "purely scientific". The project says it has supported over 30 papers and
provides an IPv6 Hitlist service.

## Behavior

TUM says it never attempts to intrude into any system, abuse vulnerabilities, guess passwords or
upload files, and only collects information about a service "as far as they are publicly visible to
everybody else on the Internet". It will not publish parts of its data that clearly identify a
person or company.

The project page says the TLS and QUIC scans run weekly: ZMap finds targets, then stateful scanners
complete handshakes, extract protocol, TLS and certificate information, "and send an HTTP request".
The TLS scans are based on Goscanner, TUM's open-source scanner. In Goscanner's code, the HTTP scan
sends a `HEAD` request for `/` unless other requests are configured (the example configuration asks
for `GET /robots.txt`).

Rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

TUM's pages give no user agent string. Goscanner's code sets this one, under the comment "Mimic
Google Chrome", since 2025-12-09:

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/140.0.0.0 Safari/537.36
```

and this one from 2023-01-19 to 2025-12-09:

```
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.134 Safari/537.36
```

Which Goscanner version the scans run is not documented.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: TUM names no `robots.txt` token and does not say whether its scans read
`robots.txt`.

To opt out, TUM says to block connection attempts from its scanning systems, or to email `scans` at
`net.in.tum.de` to be added, with the network, to its blacklist.

## IP ranges and verification

TUM's scans page lists its scanning machines in a table (HTML, no generation date), checked
2026-11-19:

- numbered hosts `planetlabX.net.in.tum.de`, IPv4 `138.246.253.X`, IPv6 `2001:4ca0:108:42::X`;
- two single hosts, `dallas` and `singapore`, each with one IPv4 and one IPv6 address.

The GINO project page has the same table, with the numbered hosts named
`planetlabX.gino-research.net.in.tum.de`. Neither page says to verify the names with reverse DNS. No
ASN is documented.

Not documented, from a DNS check on 2026-11-19: the reverse DNS names of the numbered hosts are
`planetlab<N>.gino-research.net.in.tum.de`, forward-confirmed for both IPv4 and IPv6; the
`planetlab<N>.net.in.tum.de` names resolve to the same addresses but are not the reverse DNS names.
The numbered hosts are in AS12816 (MWN, Leibniz-Rechenzentrum, the Munich scientific network). The
`dallas` and `singapore` addresses are in AS63949 (Akamai Connected Cloud, Linode); `singapore`'s
reverse DNS is `singapore.net.in.tum.de` (forward-confirmed), the `dallas` IPv4 address has a generic
Linode name and its IPv6 address none.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1, which Hyperwatch 5.7.0 depends on, returns the family `Chrome` for
both strings above.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`TUM` on a forward-confirmed hostname matching `planetlab*.gino-research.net.in.tum.de`, whatever
the user agent.

## Misc

Contact for the research group: `gino` at `net.in.tum.de`. Goscanner's source is at
https://github.com/tumi8/goscanner.

## Sources

- https://net.in.tum.de/projects/gino/scans.html (served by the scanning hosts over HTTP, checked 2026-11-19)
- https://net.in.tum.de/projects/gino/ (checked 2026-11-19)
- https://github.com/tumi8/goscanner (`scanner/scans/http.go` and its history, `example.conf`, checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
