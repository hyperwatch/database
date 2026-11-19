---
name: aidealioBot
operator: Aidealio
website: https://www.aidealio.com
documentation: https://www.aidealio.com/bot
category: search-engine
robots_txt_token: aidealioBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: aidealioBot
  identity: Aidealio
last_checked: 2026-11-19
---

# aidealioBot

## Description

aidealioBot is the crawler of Aidealio, a web search engine with its own index, which combines AI
with its own search and page quality algorithms. Aidealio says it is "starting with selected Polish
websites", and that its index is designed for more languages and places.

## Behavior

Aidealio says aidealioBot follows `robots.txt` (RFC 9309) and `Crawl-delay`, fetches at most one
page at a time per host with at least 2 seconds between requests, honours robots meta tags and
`X-Robots-Tag` (`noindex`, `nofollow`, `nosnippet`, `max-snippet`), and backs off after `429` or
`503` responses. It never fetches content behind a login or bypasses access controls. Site owners
can submit a site; each submission is reviewed by a person before the crawler visits it.

JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; aidealioBot/0.1; +https://aidealio.com/bot)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: aidealioBot
Disallow: /
```

Aidealio says it applies `robots.txt` changes within 24 hours. No other token is documented.

## IP ranges and verification

None published. Aidealio says every crawler request is signed with Web Bot Auth (HTTP Message
Signatures, RFC 9421, Ed25519), so that a site can check it comes from Aidealio. The key directory is
https://www.aidealio.com/.well-known/http-message-signatures-directory: on 2026-11-19 it held one
`OKP` / `Ed25519` key, without a `kid`, so a signature's `keyid` can only be the key's JWK
thumbprint. The `Signature-Agent` value is not documented; Hyperwatch expects
`"https://www.aidealio.com"`. No reverse DNS hostnames or ASN are documented.

Aidealio also says aidealioBot is a Cloudflare verified bot (Verified Bots, category "Search").

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 returns the family `aidealioBot`. Since Hyperwatch 5.7.0 (checked on main at
736acaf), `src/modules/identity.js` sets the identity `Aidealio`
signed only: a verified signature of `https://www.aidealio.com` (the `signedOnly` map, checked
before the rules per family) gives `Aidealio` whatever the user agent.
`https://www.aidealio.com` is in `src/data/webbotauth-agents.json`, and its one key is in
`webbotauth-keys.json`, the same as the published directory on 2026-11-19. There is no rule for the
family `aidealioBot`: without the `webbotauth` module (off by default) or without a valid signature,
the request gets no identity. This matches Aidealio's documentation, which publishes no addresses or
hostnames.

## Misc

- Aidealio offers free webmaster tools showing a site's indexed pages, the errors the crawler sees
  and the queries the site appears for: https://www.aidealio.com/webmaster.
- `https://aidealio.com/bot`, the URL in the user agent, redirects to `https://www.aidealio.com/bot`.

## Sources

- https://www.aidealio.com/bot (checked 2026-11-19)
- https://www.aidealio.com/.well-known/http-message-signatures-directory (checked 2026-11-19)
- https://www.aidealio.com/about (checked 2026-11-19)
- https://www.aidealio.com/webmaster (checked 2026-11-19)
