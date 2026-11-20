---
name: GenomeCrawlerd
operator: Nokia (Deepfield)
website: https://www.nokia.com/ip-networks/deepfield/genome/
documentation: https://www.nokia.com/genomecrawler/
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://genome.deepfield.net/crawlers.txt
  hostnames: []
hyperwatch:
  family: GenomeCrawlerd
  identity: Deepfield
last_checked: 2026-11-19
---

# GenomeCrawlerd

## Description

GenomeCrawlerd is the crawler of Nokia Deepfield Genome. Nokia describes Deepfield Secure Genome as
a "security map" of the internet that provides context for IP addresses, applications and services.
Its data feed is used for real-time network traffic analysis and for Distributed Denial of Service
(DDoS) detection and mitigation in Nokia's Deepfield Defender. Nokia says the data tracks devices and
services that can be abused for DDoS attacks (vulnerable IoT devices, misconfigured DNS servers) and
also known legitimate hosts, so that their traffic is less likely to be affected during a mitigation.

## Behavior

Nokia's page says Deepfield Genome "systematically crawls the global IPv4 and active IPv6 address
spaces, focusing on specific port ranges", and that connecting to hosts that accept connections
"might lead to protocol handshake completions" to find out what services they provide. It says the
crawling makes no attempt at unauthorized access (such as known passwords) and limits data
collection to publicly accessible information, following Nokia's privacy principles.

Paths requested, rate, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented by Nokia: its page gives no user agent string. According to Known Agents, the user
agent is:

```
Mozilla/5.0 (compatible; GenomeCrawlerd/1.0; +https://www.nokia.com/genomecrawler)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Nokia names no `robots.txt` token and does not say whether the crawler reads
`robots.txt`.

Nokia's page says the crawler's address ranges can be allowlisted or blocklisted, and gives a
contact for questions about the crawling: `genome.crawling` at `nokia.com`. No opt-out procedure is
documented.

## IP ranges and verification

Nokia's page says the "Genome crawlers operate from the following address ranges", listing two:

- `216.180.246.0/24`
- `2620:ce:e001::/48`

It links a "machine-readable prefix list" for automated allowlisting or blocklisting:
https://genome.deepfield.net/crawlers.txt, plain text, one CIDR prefix per line. On 2026-11-19 it
held 47 prefixes (14 IPv4, 33 IPv6): the two ranges above plus single addresses and small blocks.
The file gives no generation date; the server's `Last-Modified` header said 2026-11-19 10:30 UTC.

Nokia adds that "occasionally, follow-up connections may originate from IP addresses outside these
dedicated ranges". It documents no reverse DNS names and no ASN.

Not documented, from a DNS check on 2026-11-19: addresses in `216.180.246.0/24` have reverse DNS
names `crawler<NNN>.deepfield.net` (`crawler001`, `crawler010`, `crawler200`), each
forward-confirmed; their IPv6 addresses (in `2620:ce:e001::/48`) share the same names. Several
addresses of the list's other prefixes have names `monet-<NN>.crawler.deepfield.net`
(forward-confirmed), others a generic name of their hosting provider. The other prefixes are in AS12876
(Scaleway). `216.180.246.0/24` and `2620:ce:e001::/48` are announced by AS396982 (Google Cloud);
the ARIN registration of `2620:ce:e000::/44` is named `DEEPFIELD-GENOME-CRAWLERD`.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1, which Hyperwatch 5.7.0 depends on, returns the family
`GenomeCrawlerd` for the string above.

In Hyperwatch `main` (after 5.7.0, not released yet), `src/modules/identity.js` sets the identity
`Deepfield` on family `GenomeCrawlerd` from an address in Nokia Deepfield's published list
(`deepfield-ips.json`, fetched from `crawlers.txt`).

## Misc

On 2026-11-19, `https://deepfield.net/` redirected to Nokia's Deepfield product page.

## Sources

- https://www.nokia.com/genomecrawler/ (checked 2026-11-19)
- https://genome.deepfield.net/crawlers.txt (checked 2026-11-19)
- https://www.nokia.com/ip-networks/deepfield/genome/ (redirect from https://www.nokia.com/networks/technologies/deepfield-genome/, checked 2026-11-19)
- https://knownagents.com/agents/genomecrawlerd (checked 2026-11-19)
- https://rdap.org/ip/2620:ce:e001::1 (ARIN registration, checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
