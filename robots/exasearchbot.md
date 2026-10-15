---
name: ExaSearchBot
operator: Exa
website: https://exa.ai
documentation: https://crawler.exa.ai/
category: ai-search
robots_txt_token: ExaSearchBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: ExaSearchBot
  identity: Exa
last_checked: 2026-10-15
---

# ExaSearchBot

## Description

ExaSearchBot is the crawler of Exa, a search engine used by people and by applications built on
the Exa API. It discovers and indexes public web pages so that they can be found, retrieved and
cited.

## Behavior

Exa says ExaSearchBot checks `robots.txt` before fetching, crawls only public content, and does not
bypass logins, paywalls or CAPTCHAs or submit forms. It is rate-limited per site; no number is
given.

`Crawl-delay` support, JavaScript rendering and how long `robots.txt` is cached are not documented.

`robots.txt` controls crawling, not indexing. To remove a page from the index, Exa says to use a
`noindex` robots meta tag or an `X-Robots-Tag: noindex` header.

## User agents

```
Mozilla/5.0 (compatible; ExaSearchBot/1.0; +https://crawler.exa.ai/)
```

This matches the string documented by Exa.

## Observed HTTP headers

Based on dozens of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Exa by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/markdown,text/html;q=0.9,application/xhtml+xml;q=0.8,application/xml;q=0.7,image/webp;q=0.6,*/*;q=0.5` (100%) |
| `accept-language` | `en-US,en;q=0.5` (100%) |
| `cache-control` | `no-cache` (100%) |
| `pragma` | `no-cache` (100%) |
| `signature` | `(present)` (100%) |
| `signature-agent` | `"https://crawler.exa.ai"` (100%) |
| `signature-input` | `(present)` (100%) |

## Blocking with robots.txt

```
User-agent: ExaSearchBot
Disallow: /
```

ExaSearchBot first looks for a group addressed to `ExaSearchBot`. If there is none, it follows the
rules for major search engines. Otherwise it follows the `*` group.

## IP ranges and verification

None published. Exa says verification does not depend on the IP address.

Instead, requests are signed with HTTP Message Signatures (RFC 9421) following the Web Bot Auth
scheme, with Ed25519 keys. They carry `Signature`, `Signature-Input` and `Signature-Agent` headers.
The public keys are a JSON Web Key Set at
https://crawler.exa.ai/.well-known/http-message-signatures-directory (two `OKP` / `Ed25519` keys
when checked). No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS396356 Latitude.sh: `72.63.173.0/24`
- AS18779 EGIHosting: `203.100.218.0/24`
- AS47007 Colocation America Corporation: `173.46.90.0/24`
- AS16509 Amazon.com, Inc.: `32.188.113.0/24`
- AS205659 UAB code200: `216.246.215.0/24`
- AS51167 Contabo GmbH: `156.67.28.0/24`
- AS30058 FDCservers.net: `64.144.193.0/24`

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `ExaSearchBot`. In
`src/modules/identity.js`, Hyperwatch sets identity `Exa` when the request has a `Signature-Agent`
header containing `https://crawler.exa.ai`. It checks the header only; it does not validate the
signature against the key directory.

## Misc

ExaUser is Exa's second agent. It fetches a page live when a user, or an application built on the
Exa API, asks for its current content. It does not crawl, and Exa says `robots.txt` rules may not
apply to it because each fetch is user-initiated. Its requests are also signed with Web Bot Auth.
Its user agent is:

```
Mozilla/5.0 (compatible; ExaUser/1.0; +https://crawler.exa.ai/exauser)
```

Hyperwatch parses it as family `ExaUser` and gives it no identity.

Contact: support@exa.ai, preferably from an address on the domain concerned.

## Sources

- https://crawler.exa.ai/ (checked 2026-10-15)
- https://crawler.exa.ai/exauser (checked 2026-10-15)
- https://crawler.exa.ai/.well-known/http-message-signatures-directory (checked 2026-10-15)
