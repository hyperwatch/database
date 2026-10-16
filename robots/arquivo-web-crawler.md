---
name: Arquivo-web-crawler
operator: Arquivo.pt (Portuguese Web Archive)
website: https://arquivo.pt
documentation: https://arquivo.pt/faq-crawling
category: archive
robots_txt_token: Arquivo-web-crawler
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://arquivo.pt/crawlerips.json
  hostnames: []
hyperwatch:
  family: Arquivo-web-crawler
  identity: Arquivo
last_checked: 2026-10-16
---

# Arquivo-web-crawler

## Description

Arquivo-web-crawler collects pages for Arquivo.pt, the Portuguese Web Archive. Its scope is the
Portuguese Web: everything under `.pt` and other content of broad interest to the Portuguese
community. Archived pages become available one year after collection.

## Behavior

From Arquivo.pt's FAQ:

- 3 to 4 crawls of the Portuguese Web per year, about 90% of content within 7 days, plus daily
  crawls of selected publications and extra crawls around events such as elections.
- Seeds: home pages of `.pt` sites crawled before, user suggestions and the DNS listing of `.pt`
  domains. It follows links from there, with limits on size, number of contents per site and link
  depth.
- A 10-second pause between requests to the same site.
- It does not fill in forms and does not archive content behind a password.
- All media types are archived.

JavaScript rendering is not documented, although one of its user agents names browsertrix, a
browser-based crawler. `Crawl-delay` support is not documented.

## User agents

Exact strings, one per line:

```
Arquivo-web-crawler (compatible; heritrix/3.4.0-20200304 +https://arquivo.pt/faq-crawling)
Arquivo-web-crawler (compatible; brozzler/1.5 +https://arquivo.pt/faq-crawling)
Arquivo-web-crawler (compatible; browsertrix/0.8 +https://arquivo.pt/faq-crawling)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Arquivo-web-crawler
Disallow: /
```

Arquivo.pt says its crawler respects the Robots Exclusion Protocol, and the robots meta tag. It
asks site owners to allow the files needed to rebuild a page (CSS, JavaScript, images).

## IP ranges and verification

Arquivo.pt publishes its crawler ranges: `194.210.235.0/26` and `2001:690:a00:1039::/64`. The same
list is at https://arquivo.pt/crawlerips.json, a JSON object with a `creationTime` field and a
`prefixes` array of objects with `ipv4Prefix` or `ipv6Prefix` keys. On 2026-10-15 it held these 2
prefixes and was dated 2026-07-31. Arquivo.pt recommends combining the address check with the user
agent check.

Reverse DNS hostnames and ASN are not documented.

## Hyperwatch

`@hyperwatch/useragent` parses all three strings as family `Arquivo-web-crawler`. In Hyperwatch
`main` (after 5.3.3), `src/modules/identity.js` sets the identity `Arquivo` for the families
`arquivo-web-crawler` and `Arquivo-web-crawler` on an unconfirmed hostname ending with `.arquivo.pt`
or the published list (`arquivo-ips.json`, 2 entries). Arquivo.pt does not document this hostname.

## Misc

Problems can be reported to Arquivo.pt with the full user agent, the dates of access and a
description. Anyone can save a page to the archive with its SavePageNow service.

## Sources

- https://sobre.arquivo.pt/en/help/crawling-and-archiving-web-content/ (checked 2026-10-15, reached from https://arquivo.pt/faq-crawling)
- https://arquivo.pt/crawlerips.json (checked 2026-10-15)
- https://sobre.arquivo.pt/en/recommendations-for-authors-to-enable-web-archiving/robots-exclusion-protocol-authorizing-the-harvest-of-important-content/ (checked 2026-10-15)
