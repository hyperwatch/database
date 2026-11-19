---
name: KamataBot
operator: Kamata
website: https://www.kamata.ai
documentation: https://api.kamata.ai/bot
category: marketing
robots_txt_token: KamataBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: KamataBot
  identity: Kamata
last_checked: 2026-11-19
---

# KamataBot

## Description

KamataBot is the crawler of Kamata, which sells B2B outbound sales: it scans public records for
companies with a reason to buy, reaches decision-makers and books meetings. Kamata says KamataBot
reads the public pages a business publishes about itself "so we can describe companies accurately
for B2B research": what a company does, its size and location, its open roles and the team it lists
publicly.

## Behavior

Kamata says KamataBot fetches only public pages about the business: `robots.txt` and the sitemap,
the home page, and a few pages such as about, team, careers, products, customers and contact. It
does not crawl whole sites. It makes one request at a time with pauses between them, honours
`Crawl-delay`, slows down when a site answers slowly, and backs off on `429` or `5xx`. It comes back
when pages are likely to have changed, usually every few weeks.

It never logs in, fills in or submits forms, reads anything behind a password, solves CAPTCHAs or
tries to get past anti-bot challenges, and Kamata says it does not disguise the crawler as a browser
or switch addresses to avoid a block. A page that answers with a challenge or a refusal is not
requested again for days; for that page Kamata may use the Common Crawl archive's copy, labelled with
its capture date, but never for a page `robots.txt` closes to KamataBot.

JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; KamataBot/1.0; +https://api.kamata.ai/bot)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: KamataBot
Disallow: /
```

Kamata says `User-agent: *` with `Disallow: /` also blocks it, path rules work as usual, and changes
are picked up within a day. No other token is documented.

## IP ranges and verification

None published. Kamata says every request is signed with HTTP Message Signatures ("Web Bot Auth").
The key directory is https://api.kamata.ai/.well-known/http-message-signatures-directory: on
2026-11-19 it held one `OKP` / `Ed25519` key, without a `kid`, so a signature's `keyid` can only be
the key's JWK thumbprint. The `Signature-Agent` value is not documented; Hyperwatch expects
`"https://api.kamata.ai"`. No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 returns the family `KamataBot`. Since Hyperwatch 5.7.0 (checked on main at
736acaf), `src/modules/identity.js` sets the identity `Kamata`
signed only: a verified signature of `https://api.kamata.ai` (the `signedOnly` map, checked before
the rules per family) gives `Kamata` whatever the user agent. `https://api.kamata.ai` is in
`src/data/webbotauth-agents.json`, and its one key is in `webbotauth-keys.json`, the same as the
published directory on 2026-11-19. There is no rule for the family `KamataBot`: without the
`webbotauth` module (off by default) or without a valid signature, the request gets no identity.
This matches Kamata's documentation, which publishes no addresses or hostnames.

## Misc

- Contact: crawler@kamata.ai, with the domain concerned.

## Sources

- https://api.kamata.ai/bot (checked 2026-11-19)
- https://api.kamata.ai/.well-known/http-message-signatures-directory (checked 2026-11-19)
- https://www.kamata.ai/ (checked 2026-11-19)
