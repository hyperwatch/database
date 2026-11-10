---
name: ICC-Crawler
operator: National Institute of Information and Communications Technology (NICT), Universal Communication Research Institute
website: https://ucri.nict.go.jp/en/
documentation: https://ucri.nict.go.jp/en/icccrawler.html
category: research
robots_txt_token: ICC-Crawler
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://ucri.nict.go.jp/en/icccrawler.html
  hostnames: []
hyperwatch:
  family: ICC-Crawler
  identity: NICT
last_checked: 2026-11-10
---

# ICC-Crawler

## Description

ICC-Crawler is the web crawler of the Universal Communication Research Institute at Japan's
National Institute of Information and Communications Technology (NICT). NICT uses the pages it
collects for research and development in multilingual translation, information analysis and
artificial intelligence, and may provide them, or what it builds from them, to third parties
(private companies and public institutions) for joint research or their own use.

## Behavior

NICT says it monitors the number of connections per unit of time to avoid excessive load, and
schedules connections so as not to overload a host even when it uses several addresses or
hostnames. It stops collecting from a host or address on request.

With a `Crawl-delay`, it waits the larger of that delay and its own minimum interval. JavaScript
rendering and how often `robots.txt` is read are not documented.

## User agents

Exact strings, one per line:

```
ICC-Crawler/3.0 (Mozilla-compatible; ; https://ucri.nict.go.jp/en/icccrawler.html)
```

## Observed HTTP headers

Based on hundreds of requests seen between 2026-11-09 and 2026-11-10, nearly all pages, from the
published address.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html;q=0.9,*/*;q=0.5` (99%) |
| `accept-language` | `ja` (99%) |

## Blocking with robots.txt

```
User-agent: ICC-Crawler
Disallow: /
```

NICT says ICC-Crawler follows the Robots Exclusion Protocol (RFC 9309), including `Allow` and `*`
patterns, and documents examples for disallowing paths and file types. If it keeps coming after a
`Disallow`, NICT asks to be contacted.

## IP ranges and verification

NICT lists two addresses on the documentation page: `202.180.34.186` and `61.86.246.72`. There is
no machine-readable list and no date. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-11-09 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Reverse DNS hostnames:

- `gw.ucri.jgn-x.jp` (forward-confirmed, the published address `202.180.34.186`)

## Hyperwatch

`@hyperwatch/useragent` returns the family `ICC-Crawler`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` sets the identity `NICT` when the address is in the inline ranges
`202.180.34.186/32` and `61.86.246.72/32`, NICT's two documented addresses. NICT publishes no
machine-readable list, so a change on its documentation page needs a change in the code.

## Misc

NICT says pages collected before 2024-07-11 are handled under different terms, described on a
linked page.

Contact: Common Infrastructure Group, General Planning Office, Universal Communication Research
Institute, NICT (phone and fax on the documentation page).

## Sources

- https://ucri.nict.go.jp/en/icccrawler.html (checked 2026-11-10)
