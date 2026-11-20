---
name: Shodan
operator: Shodan
website: https://www.shodan.io
documentation: https://book.shodan.io/behind-the-scenes/crawler-algorithm/
category: research
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: Shodan
last_checked: 2026-11-19
---

# Shodan

## Description

Shodan is "a search engine for Internet-connected devices". Its crawlers query devices directly
connected to the internet and index their banners, the metadata a service sends before a client
interacts with it (server software, options, welcome message). The data is used for network
security, market research, cyber risk, Internet of Things tracking and ransomware tracking. The
company behind it is not named on the pages checked (footer: "Shodan ® - All rights reserved").

## Behavior

According to Shodan's book, the crawlers run 24/7 from locations around the world, so that
country-wide blocking does not affect data collection. The basic algorithm picks a random IPv4
address and a random port from those Shodan understands, grabs the banner and starts again, and is
designed to crawl the internet once a week; assets configured on Shodan Monitor are rescanned at
least once a day. Crawlers detect when a port runs another protocol than expected. At the start of
every month, Shodan runs a hostname-based scan of all websites it knows about, with the `Host` and
SNI headers set to the hostname instead of the address. Banners listing other hosts (DHT peers, for
instance) can trigger "cascading" scans of those hosts.

Paid users can also request on-demand scans of an address or network through the API; an address
crawled recently is not rescanned within 24 hours, except with an Enterprise subscription.

Which HTTP paths are requested, JavaScript rendering and `robots.txt` handling are not documented.

## User agents

Not documented. Shodan's help center, developer documentation and book give no user agent string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Shodan names no `robots.txt` token and does not say whether its crawlers read
`robots.txt`. No opt-out or exclusion procedure was found on its help center, developer
documentation or book; the help center gives `support@shodan.io` as its contact address.

## IP ranges and verification

None published. Shodan documents no IP list, reverse DNS names or ASN.

Not documented, from a DNS check on 2026-11-19: a crawler address had the reverse DNS name
`flower.census.shodan.io`, which resolves back to the same address (forward-confirmed). The address
is in AS202425 (`INT-NETWORK IP Volume inc`), which Shodan does not document. The pattern
`*.census.shodan.io` fits that name; it rests on one observed name only.

## Hyperwatch

No user agent is documented, so no agent family can be given.

In Hyperwatch `main` (after 5.7.0, not released yet), the "hostname only" fallback sets the identity
`Shodan` on a forward-confirmed hostname matching `*.census.shodan.io`, whatever the user agent.

## Misc

Nothing documented.

## Sources

- https://help.shodan.io/the-basics/what-is-shodan (checked 2026-11-19)
- https://help.shodan.io/the-basics/on-demand-scanning (checked 2026-11-19)
- https://help.shodan.io/ (checked 2026-11-19)
- https://book.shodan.io/behind-the-scenes/crawler-algorithm/ (checked 2026-11-19)
- https://developer.shodan.io/api (checked 2026-11-19)
- https://www.shodan.io/ (checked 2026-11-19)
- Reverse and forward DNS lookups through 1.1.1.1 and 8.8.8.8 (checked 2026-11-19)
