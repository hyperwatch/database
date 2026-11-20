---
name: BinaryEdge
operator: Coalition, Inc.
website: https://www.coalitioninc.com
documentation: https://help.coalitioninc.com/hc/en-us/articles/48928737389979-What-the-BinaryEdge-scanner-does-and-why-Coalition-may-scan-your-internet-facing-systems
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: both
  ip_list: https://api.binaryedge.io/v1/minions
  hostnames: [".binaryedge.ninja"]
hyperwatch:
  family: null
  identity: BinaryEdge
last_checked: 2026-11-19
---

# BinaryEdge

## Description

BinaryEdge is an internet scanning engine owned by Coalition, Inc., which acquired it in 2020
("BinaryEdge is a registered trademark of Coalition, Inc."). The standalone BinaryEdge platform shut
down on March 31, 2025; its scanning engine now feeds Coalition Control, Coalition's cyber risk
management platform, and Coalition's cyber insurance underwriting. Coalition says it does not sell
the scan data as a product.

The operator's pages could not be read live on 2026-11-19: `docs.binaryedge.io` and
`www.binaryedge.io` redirect to two articles of Coalition's help center that now return 404 (the
help center has moved and the articles are not in its new sitemap). Everything below comes from
the Internet Archive's copies of those articles (captured 2026-09-28 and 2026-10-07, both updated
2026-04-09) and of `https://docs.binaryedge.io/SEv2/blocking/` (captured 2026-01-09), except the
address lists, which were fetched live.

## Behavior

According to Coalition's article, the scan engine looks for open ports, exposed services and
protocols, service metadata and technology, device or version indicators (CPE). It covers
"hundreds of important ports" chosen from attacker activity, new vulnerabilities and research, not
every port. Scanning is "effectively continuous", with a full refresh of public addresses about
every 30 days and more frequent rescans of some ports. The BinaryEdge documentation describes a
coordinator, "Krang", and thousands of scanning hosts, "Minions".

Which HTTP paths are requested, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. The pages give no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: BinaryEdge names no `robots.txt` token and does not say whether it reads
`robots.txt`.

To be excluded from scans, email `support@binaryedge.io` with the IP addresses to exclude.
The older BinaryEdge documentation also asked for the requester's name and organization and the
date, time and addresses of the traffic received, and recommended this over blocking because its
scanning hosts are ephemeral.

## IP ranges and verification

Coalition's article says the scanners "publish reverse DNS entries in the binaryedge.ninja domain"
and that the current scanner addresses are available through the API. It does not say to confirm
the name with a forward lookup.

Published lists:

- IPv4: https://api.binaryedge.io/v1/minions, JSON `{"scanners": [...], "md5": [...]}`. On
  2026-11-19, `scanners` held 4,458 single IPv4 addresses (no prefixes) and `md5` 68 hashes, whose
  meaning is not documented. The list has no generation date; its `Last-Modified` header was
  `Wed, 18 Nov 2026 19:33:18 GMT`.
- IPv6: https://api.binaryedge.io/v1/minions-ipv6, same format, 3,098 single IPv6 addresses and 68
  hashes on 2026-11-19, `Last-Modified: Wed, 18 Nov 2026 19:33:23 GMT`.

The endpoints are rate-limited (HTTP 429 when requested too often). The documentation calls the list
"up-to-the-moment" and warns that addresses are not tied to the scanning hosts over the long term.
The v2 list it also names, `https://api.binaryedge.io/krang/v1/minions`, returned 404 on 2026-11-19.

No ASN is documented.

Not documented, from a DNS check on 2026-11-19: a scanner address listed in the IPv4 list had the
reverse DNS name `us-east-39.barium.li.prod.binaryedge.ninja`, which resolves back to the same
address (forward-confirmed). The address is in AS63949 (`AKAMAI-LINODE-AP - Akamai Connected
Cloud`), a cloud provider's network.

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`BinaryEdge` on a forward-confirmed hostname ending with `.binaryedge.ninja` (any name under that
domain, whatever its depth), whatever the user agent.

## Misc

Former BinaryEdge customers are directed to `binaryedgesupport@coalitioninc.com` and to Coalition
Control.

## Sources

- https://help.coalitioninc.com/hc/en-us/articles/48928737389979-What-the-BinaryEdge-scanner-does-and-why-Coalition-may-scan-your-internet-facing-systems (redirect from https://docs.binaryedge.io/, checked 2026-11-19: 404)
- https://web.archive.org/web/20260928183133/https://help.coalitioninc.com/hc/en-us/articles/48928737389979-What-the-BinaryEdge-scanner-does-and-why-Coalition-may-scan-your-internet-facing-systems (checked 2026-11-19)
- https://help.coalitioninc.com/hc/en-us/articles/34383910057371-BinaryEdge-Transition-FAQ (redirect from https://www.binaryedge.io/, checked 2026-11-19: 404)
- https://web.archive.org/web/20261007045831/https://help.coalitioninc.com/hc/en-us/articles/34383910057371-BinaryEdge-Transition-FAQ (checked 2026-11-19)
- https://web.archive.org/web/20260109070050/https://docs.binaryedge.io/SEv2/blocking/ (checked 2026-11-19)
- https://api.binaryedge.io/v1/minions (checked 2026-11-19)
- https://api.binaryedge.io/v1/minions-ipv6 (checked 2026-11-19)
- https://api.binaryedge.io/krang/v1/minions (checked 2026-11-19: 404)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
