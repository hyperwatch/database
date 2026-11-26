---
name: PoliasBot
operator: Polias
website: https://polias.eu
documentation: https://polias.eu/bot
category: search-engine
robots_txt_token: PoliasBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://polias.eu/bot/ips.json
  hostnames: []
hyperwatch:
  family: PoliasBot
  identity: Polias
last_checked: 2026-11-25
---

# PoliasBot

## Description

PoliasBot is the crawler of Polias, a search engine from Germany ("Die Suchmaschine aus Europa",
in beta, starting with German-speaking countries). Polias says PoliasBot "collects public web pages
for the search index of Polias".

## Behavior

From Polias's page:

- It respects `robots.txt` (rules for `PoliasBot`, otherwise `*`) and `Crawl-delay`.
- It fetches one page after another, with pauses: one site per server at a time, at least one
  second between requests, longer on slow servers; it ends the visit when a server refuses it
  several times.
- It never submits forms or logs in.
- Since 23 November 2026: it waits and slows down on "too many requests" or "temporarily
  unavailable", fetches nothing from a site whose `robots.txt` returns a server error, respects
  `noindex` and `nofollow` in `X-Robots-Tag`, and records TDMRep reservations (Polias then gives no
  excerpt of those pages for news and AI answers).

JavaScript rendering and how long `robots.txt` is cached are not documented.

## User agents

Exact strings, one per line:

```
PoliasBot/0.1 (+https://polias.eu/bot; hallo@polias.eu)
```

This matches the example on Polias's page, which says the user agent contains `PoliasBot`.

## Observed HTTP headers

```
accept: text/html
accept-language: en, *;q=0.3
user-agent: PoliasBot/0.1 (+https://polias.eu/bot; hallo@polias.eu)
```

## Blocking with robots.txt

```
User-agent: PoliasBot
Disallow: /
```

It follows the `PoliasBot` group, or the `*` group when there is none. Polias also removes a site
from its index on request (hallo@polias.eu).

## IP ranges and verification

- IP list: https://polias.eu/bot/ips.json, linked from the robot's page. JSON object with
  `creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` and `{"ipv6Prefix": ...}`
  objects. On 2026-11-25 it held two prefixes, `162.55.103.77/32` and `2a01:4f8:271:59a1::2/128`,
  with `creationTime` 2026-11-05.
- Polias says PoliasBot also crawls "from rented extra servers whose addresses change, so it is
  best recognised by its user agent": requests from those servers can't be verified.
- Reverse DNS: not documented.
- ASN: not documented.
- Web Bot Auth: not documented.

### Observed

Requests came from both listed addresses.

## Hyperwatch

`@hyperwatch/useragent` returns the family `PoliasBot`. Hyperwatch's `src/modules/identity.js`
sets the identity `Polias` for the family `PoliasBot` on the published list (`poliasbot-ips.json`,
2 prefixes, fetched from the URL above), from
[hyperwatch/hyperwatch#781](https://github.com/hyperwatch/hyperwatch/pull/781) (not released yet).
Requests from Polias's unlisted extra servers get no identity.

## Misc

- Polias also runs **Polias-KI**, which opens single pages only when a user asks a question in the
  Polias chat and doesn't store them in the index. It follows the `robots.txt` rules for
  `Polias-KI`, then `PoliasBot`, then `*`. Its user agent and addresses are not documented.
- Contact for problems and removals: hallo@polias.eu.

## Sources

- https://polias.eu/bot (checked 2026-11-25)
- https://polias.eu/bot/ips.json (checked 2026-11-25)
- https://polias.eu/ (checked 2026-11-25)
