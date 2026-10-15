---
name: ExaSearchBot
operator: Exa
website: https://exa.ai
documentation: https://crawler.exa.ai/
category: ai-search
robots_txt_token: ExaSearchBot
respects_robots_txt: yes
verification:
  method: none
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

<!-- observed headers: to be filled -->

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
