---
name: ExaUser
operator: Exa
website: https://exa.ai
documentation: https://exauser.crawler.exa.ai/
category: ai-assistant
robots_txt_token: null
respects_robots_txt: partial
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: ExaUser
  identity: Exa
last_checked: 2026-11-12
---

# ExaUser

## Description

ExaUser is Exa's user-triggered fetcher. Exa uses it to fetch a page live when a user, or an
application built on the Exa API, asks for its current content. It is not Exa's crawler: that is
[ExaSearchBot](exasearchbot.md).

## Behavior

Exa says ExaUser fetches a page only when a user asks for it, with no scheduled or background
crawling. It only accesses public content, and does not bypass logins, paywalls or CAPTCHAs or
submit forms. It does not decide whether content can appear in Exa search. Images are fetched as a
separate agent, ExaUser-Images.

Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ExaUser/1.0; +https://exauser.crawler.exa.ai)
```

This is the documented string.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-11-12, pages, verified as Exa by Hyperwatch 5.6.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/markdown,text/html;q=0.9,application/xhtml+xml;q=0.8,application/xml;q=0.7,image/webp;q=0.6,*/*;q=0.5` (100%) |
| `accept-language` | `en-US,en;q=0.5` (100%) |
| `cache-control` | `no-cache` (100%) |
| `pragma` | `no-cache` (100%) |
| `signature` | `(present)` (100%) |
| `signature-agent` | `"https://exauser.crawler.exa.ai"` (100%) |
| `signature-input` | `(present)` (100%) |

The signatures cover `@authority` and `signature-agent`, with `tag="web-bot-auth"`,
`alg="ed25519"` and a nonce.

## Blocking with robots.txt

Not documented: Exa names no `robots.txt` token for ExaUser. Exa says "Because fetches are initiated
by a user, robots.txt rules may not apply", and points to the `ExaSearchBot` token for search
opt-outs and automatic crawling:

```
User-agent: ExaSearchBot
Disallow: /
```

## IP ranges and verification

None published. Exa says every request is signed with Web Bot Auth (RFC 9421), verified
automatically by Cloudflare, Akamai and other providers that support it. The public keys are at
https://exauser.crawler.exa.ai/.well-known/http-message-signatures-directory: on 2026-11-12 it held
one `OKP` / `Ed25519` key. Its `kid` is the key's JWK thumbprint, and the `keyid` of the signatures
seen is that thumbprint. The `Signature-Agent` value is not documented; the requests seen sent
`"https://exauser.crawler.exa.ai"`. No reverse DNS hostnames or ASN are documented.

### Observed

Requests verified as Exa with this user agent seen on 2026-11-12. The operator publishes no ranges
or hostnames.

Networks:

- AS396356 Latitude.sh: `72.63.173.0/24`

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `ExaUser`. In Hyperwatch 5.6.0,
`src/modules/identity.js` has no rule for this family: it sets the identity `Exa` on a verified
signature of `https://exauser.crawler.exa.ai`, whatever the user agent ("signed only", the
`signedOnly` map, checked before the rules per family). `https://exauser.crawler.exa.ai` is in
`src/data/webbotauth-agents.json`, and its one key is in `webbotauth-keys.json`, the same as the
published directory on 2026-11-12. This needs the `webbotauth` module, off by default; without it,
Hyperwatch gives ExaUser no identity, and the `Signature-Agent` header alone is not checked for it.
ExaUser-Images is not in `webbotauth-agents.json`.

## Misc

- ExaUser-Images has its own page, https://exauser-images.crawler.exa.ai/; its user agent and key
  directory are not given on ExaUser's page.
- Contact: support@exa.ai, preferably from an address on the domain concerned.

## Sources

- https://exauser.crawler.exa.ai/ (checked 2026-11-12)
- https://exauser.crawler.exa.ai/.well-known/http-message-signatures-directory (checked 2026-11-12)
