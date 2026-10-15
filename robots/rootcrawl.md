---
name: RootCrawl
operator: RootCrawl (operated by DataChaser)
website: https://rootcrawl.org
documentation: https://rootcrawl.org/bot
category: archive
robots_txt_token: RootCrawl
respects_robots_txt: partial
verification:
  method: web-bot-auth
  ip_list: https://rootcrawl.org/.well-known/rootcrawl-crawler-ips.json
  hostnames:
    - .rootcrawl.org
hyperwatch:
  family: RootCrawl
  identity: null
last_checked: 2026-10-15
---

# RootCrawl

## Description

RootCrawl builds a public archive of website homepages. It fetches only the root path (`/`) of each
registered domain, stores the HTML compressed, and makes it available free for academic and
research use. RootCrawl says it is not a search engine and does not crawl sub-pages, media or
forms. It is operated by DataChaser.

## Behavior

From the operator's page, updated 18 September 2026:

- One `GET` request for `/` per domain, following up to 3 redirects. No assets, no forms, no
  authentication attempts.
- A domain is re-fetched at most once every three months. The home page says the archive is
  refreshed monthly.
- Globally rate-limited, 10-second request timeout. Repeated failures, `429` or `503` take a domain
  out of rotation.
- The crawler was paused as of 18 September 2026. Automated `robots.txt` enforcement was "being
  finished" and due before the next crawl run. Until then, exclusion requests sent by mail are
  applied by hand.

JavaScript rendering and `Crawl-delay` support are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; RootCrawl/1.0; +https://rootcrawl.org/bot)
```

A copy of the home page archived on 2026-02-13 gives
`Mozilla/5.0 (compatible; RootCrawl/1.0; +https://rootcrawl.org)`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

The operator says every request carries the `Signature-Agent`, `Signature-Input` and `Signature`
headers (see below).

## Blocking with robots.txt

```
User-agent: RootCrawl
Disallow: /
```

RootCrawl also says it will not route around a block on its `Signature-Agent` header or its
addresses, and keeps a permanent exclusion list for domains sent by mail.

## IP ranges and verification

RootCrawl says the user agent should not be trusted and recommends checking the signature. Every
request is signed with Ed25519 under Web Bot Auth (RFC 9421 HTTP Message Signatures), tag
`web-bot-auth`, covering `@authority` and `signature-agent`, with a five-minute validity window. The
key directory is https://rootcrawl.org/.well-known/http-message-signatures-directory. On 2026-10-15
it held one key, ID `IkXmhDbJmDVtmvSawe59edaeKKH35uTlnhYWWCHPqcE`.

Addresses are published at https://rootcrawl.org/.well-known/rootcrawl-crawler-ips.json, a JSON
object with an `updated` field and a `prefixes` array of objects with `ipv4Prefix` or `ipv6Prefix`
keys. On 2026-10-15 it held 5 prefixes (4 IPv4 `/32`, 1 IPv6 `/64`) and was dated 2026-09-18.

RootCrawl also says every crawling address resolves to a `*.rootcrawl.org` name that resolves back
to the same address. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `RootCrawl`. `src/modules/identity.js`
has a rule for the family `RootCrawl-Crawler`, which no documented user agent produces, so the
documented crawler never gets the identity `RootCrawl`. For a request that did parse as
`RootCrawl-Crawler`, the rule checks that the reverse DNS name ends with `.rootcrawl.org`, without
a forward lookup. It does not use the signature, the IP list or the forward-confirmed hostname.

## Misc

Abuse reports and rate complaints go to the contact address on the bot page, which RootCrawl says
is answered by a human.

## Sources

- https://rootcrawl.org/bot (checked 2026-10-15)
- https://rootcrawl.org/ (checked 2026-10-15)
- https://rootcrawl.org/.well-known/rootcrawl-crawler-ips.json (checked 2026-10-15)
- https://rootcrawl.org/.well-known/http-message-signatures-directory (checked 2026-10-15)
- https://web.archive.org/web/20260213173742/https://rootcrawl.org/ (checked 2026-10-15)
