---
name: AIWebIndex
operator: Aleksma Ai, Inc. (Lyrenth)
website: https://lyrenth.com
documentation: https://lyrenth.com/bot
category: ai-search
robots_txt_token: AIWebIndex
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://lyrenth.com/bot/ip-ranges.json
  hostnames:
    - lyrenth.com
hyperwatch:
  family: AIWebIndex
  identity: Lyrenth
last_checked: 2026-10-15
---

# AIWebIndex

## Description

AIWebIndex is the crawler that builds Lyrenth, "the AI-readable web index", run by Aleksma Ai, Inc.
Lyrenth serves each indexed page to AI agents as a JSON document through an API. Lyrenth says the
crawler "is an indexer, not a model trainer: we do not train foundation models on the content we
crawl". On-demand fetches, made when a customer asks the index for a specific URL, use a separate
user agent, AIWebIndex-Agent.

## Behavior

Lyrenth says the crawler:

- implements RFC 9309 and honors `Disallow`, `Crawl-delay`, `Sitemap` and HTTP 429/503 backoff;
- fetches at most once every 2 seconds per domain across its fleet, or at the `Crawl-delay` when
  longer;
- "fails closed when robots.txt cannot be read";
- reads links only from a parsed HTML document, refuses known honeypot paths and flags links hidden
  from human readers.

AIWebIndex-Agent fetches "honor robots.txt the same way". JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
AIWebIndex/2.0 (+https://lyrenth.com/bot; AI-readable web index)
AIWebIndex-Agent/2.0 (+https://lyrenth.com/bot; on-demand index fetch)
AIWebIndex/2.0 verification (+https://lyrenth.com/bot)
```

The third string is used for domain ownership checks, which fetch
`/.well-known/aiwebindex-verify.txt` over HTTPS for site owners who verify their domain.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: AIWebIndex
Disallow: /
```

This is Lyrenth's opt-out example. Lyrenth does not say whether a group naming `AIWebIndex` also
applies to AIWebIndex-Agent, or whether `AIWebIndex-Agent` can be named on its own.

## IP ranges and verification

Lyrenth documents three checks:

1. The address is in https://lyrenth.com/bot/ip-ranges.json (served from `www.lyrenth.com`): an
   object with `creationTime`, `policy`, `contact`, `userAgents` and a `prefixes` array of
   `{"ipv4Prefix": ...}` objects. On 2026-10-15 it held 22 IPv4 prefixes, all `/32`, with
   `creationTime` 2026-08-16. It lists the first two user agents above.
2. Requests carry a Web Bot Auth signature (RFC 9421); the key directory is
   https://api.lyrenth.com/.well-known/http-message-signatures-directory (one Ed25519 key on
   2026-10-15).
3. Every address has forward-confirmed reverse DNS under `lyrenth.com`.

No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `AIWebIndex` for the first and third strings and
`AIWebIndex-Agent` for the second. In Hyperwatch `main` (after 5.3.3), `src/modules/identity.js`
sets the identity `Lyrenth` for both families on an unconfirmed hostname ending with `.lyrenth.com`
or the published list (`lyrenth-ips.json`). The code comment says forward-confirmed, but the rule
reads `hostname`, not `verifiedHostname`, so the forward lookup Lyrenth documents is not checked.
The Web Bot Auth signatures are not checked either.

## Misc

- Lyrenth's contact is hello@lyrenth.com.

## Sources

- https://lyrenth.com/bot (checked 2026-10-15, redirects to https://www.lyrenth.com/bot)
- https://lyrenth.com/bot/ip-ranges.json (checked 2026-10-15)
- https://api.lyrenth.com/.well-known/http-message-signatures-directory (checked 2026-10-15)
