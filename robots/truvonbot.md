---
name: TruvonBot
operator: Truvon
website: https://truvon.ai
documentation: https://truvon.ai/bot
category: ai-search
robots_txt_token: TruvonBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: TruvonBot
  identity: Truvon
last_checked: 2026-11-19
---

# TruvonBot

## Description

TruvonBot is the crawler of Truvon, which keeps a dated record of U.S. businesses for AI assistants
("checked, dated facts about businesses, for every AI"). TruvonBot reads a business's own website
"so the record says what the business says, not only what directories copied".

## Behavior

Truvon says TruvonBot reads the home page, `robots.txt` and the sitemap; files written for AI and
agents if the site has them (`llms.txt`, an agent card, an MCP or OpenAPI description, a UCP or API
catalog, `security.txt`); up to four of the site's own pages about what it offers that the home page
links to, and up to two of their PDFs; and, when the home page states no hours, the page its links
say holds them. It reads at most 600 KB of a page and waits at most 12 seconds for one. A visit is
about 17 requests, plus up to seven for those pages.

It visits when a business is first listed, about once a month after that, and when the owner asks
for a new check. It never fills in forms, signs in, buys or books, and does not run a page's
scripts.

`Crawl-delay` support and how long `robots.txt` is cached are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; TruvonBot/1.0; +https://truvon.ai/bot)
```

This is the documented string; Truvon says every request carries it.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: TruvonBot
Disallow: /
```

Truvon says its crawl follows `robots.txt` as RFC 9309 sets out: a group naming `TruvonBot`, or
otherwise the `*` group. A missing `robots.txt` allows everything; one that fails (a server error or
no answer) keeps it out until the next visit. A read of one site that a person asks for, such as an
owner listing their own business, is "a visit on their behalf, not a crawl"; Truvon does not say
whether such a read follows `robots.txt`. Blocking TruvonBot keeps the business listed from public
sources; to be removed from Truvon altogether, the owner writes to support@truvon.ai.

## IP ranges and verification

None published. Truvon says TruvonBot signs every request with Web Bot Auth (HTTP Message
Signatures, RFC 9421, Ed25519), with the `Signature-Agent` `"https://truvon.ai"`, and that a host
checking signatures "can let in TruvonBot and nothing that only copies its name". The key directory
is https://truvon.ai/.well-known/http-message-signatures-directory: on 2026-11-19 it held 2 `OKP` /
`Ed25519` keys, each with a `kid` equal to the key's JWK thumbprint (and `alg` and `use` fields), so
the `keyid` is both. No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 returns the family `TruvonBot`. Since Hyperwatch 5.7.0 (checked on main at
736acaf), `src/modules/identity.js` sets the identity `Truvon`
signed only: a verified signature of `https://truvon.ai` (the `signedOnly` map, checked before the
rules per family) gives `Truvon` whatever the user agent. `https://truvon.ai` is in
`src/data/webbotauth-agents.json`, and its two keys are in `webbotauth-keys.json`, the same as the
published directory on 2026-11-19. There is no rule for the family `TruvonBot`: without the
`webbotauth` module (off by default) or without a valid signature, the request gets no identity.
This matches Truvon's documentation, which publishes no addresses or hostnames.

## Misc

- Truvon's page explains how to let TruvonBot through common hosts and security tools (WordPress
  plugins, Wix, Squarespace, Shopify, Webflow, Cloudflare), and recommends rules that check its
  signature over rules that trust its user agent.
- Contact: support@truvon.ai.

## Sources

- https://truvon.ai/bot (checked 2026-11-19)
- https://truvon.ai/.well-known/http-message-signatures-directory (checked 2026-11-19)
- https://truvon.ai/ (checked 2026-11-19)
