---
name: OctenSearchBot
operator: Octen
website: https://octen.ai
documentation: https://crawler.octen.ai/
category: ai-search
robots_txt_token: OctenSearchBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: OctenSearchBot
  identity: Octen
last_checked: 2026-11-12
---

# OctenSearchBot

## Description

OctenSearchBot is the crawler of Octen, which sells web search APIs for AI applications ("Search
infrastructure for AI"). Octen says it "uses a robot (OctenSearchBot) to discover and index pages on
the public web", so that users and applications can "find, retrieve, and cite" them.

## Behavior

Octen says OctenSearchBot checks `robots.txt` before fetching, crawls only public content, does not
attempt to bypass logins, paywalls or CAPTCHAs, and submits no forms. It is "rate-limited per site";
no number is given.

`Crawl-delay` support, JavaScript rendering and how long `robots.txt` is cached are not documented.

`robots.txt` controls crawling, not indexing. To keep a page out of the index, Octen says to use a
`noindex` robots meta tag or an `X-Robots-Tag: noindex` header.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; OctenSearchBot/1.0; +https://crawler.octen.ai/)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: OctenSearchBot
Disallow: /
```

OctenSearchBot looks for a group addressed to `OctenSearchBot`; if there is none, it follows the `*`
group. No other token is documented.

## IP ranges and verification

None published. Octen says verification is cryptographic and "holds regardless of the request's IP
address".

Every request is signed with HTTP Message Signatures (RFC 9421) following the Web Bot Auth scheme,
with Ed25519 keys, and carries `Signature`, `Signature-Input` and a `Signature-Agent` header. The
`Signature-Agent` value is `"https://crawler.octen.ai"`. The key directory is
https://crawler.octen.ai/.well-known/http-message-signatures-directory: on 2026-11-12 it held 2
`OKP` / `Ed25519` keys, each with a `kid` equal to the key's JWK thumbprint, so the `keyid` is both.
The directory's own response was signed with both keys. No reverse DNS hostnames or ASN are
documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.0 returns the family `OctenSearchBot`. In Hyperwatch 5.6.0,
`src/modules/identity.js` sets the identity `Octen` signed only: a verified signature of
`https://crawler.octen.ai` (the `signedOnly` map, checked before the rules per family) gives
`Octen` whatever the user agent. `https://crawler.octen.ai` is in `src/data/webbotauth-agents.json`,
so Hyperwatch fetches its key directory. There is no rule for the family `OctenSearchBot`: without
the `webbotauth` module (off by default) or without a valid signature, the request gets no identity.
This matches Octen's documentation, which publishes no addresses or hostnames.

## Misc

Contact: crawler@octen.ai, preferably from an address on the domain concerned, with the affected
URL, the time of the requests and relevant log lines.

## Sources

- https://crawler.octen.ai/ (checked 2026-11-12)
- https://crawler.octen.ai/.well-known/http-message-signatures-directory (checked 2026-11-12)
- https://octen.ai/ (checked 2026-11-12)
