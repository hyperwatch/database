---
name: RiverBot
operator: River AI Inc.
website: https://river.ai
documentation: https://river.ai/bot
category: ai-training
robots_txt_token: RiverBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://river.ai/riverbot.json
  hostnames:
    - "*.bot.river.ai"
hyperwatch:
  family: RiverBot
  identity: River
last_checked: 2026-11-10
---

# RiverBot

## Description

RiverBot is the web crawler of River (River AI Inc.). It fetches public web pages that River uses
to train and evaluate its AI models.

## Behavior

River says RiverBot makes one request at a time to each site, starting at no more than one request
per second and never more than two, unless the site's owner agreed to more. It slows down when a
site responds slowly or with server errors; a `429` or `503` makes it wait for `Retry-After` and
crawl that site more slowly from then on.

It fetches only the pages it was given and the redirects they lead to, each checked against
`robots.txt`. It does not follow links from page to page, run JavaScript, submit forms or log in.
If a site answers with a challenge page or keeps refusing it with `403` errors, it stops crawling
that site until someone at River has looked at it.

River says it never imitates a browser and does not switch addresses to get around a block.
Changes to RiverBot, its addresses included, are announced in an Atom feed
(https://river.ai/bot.atom).

## User agents

Exact strings, one per line:

```
RiverBot/1.0 (+https://river.ai/bot)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: RiverBot
Disallow: /
```

RiverBot follows the group that names it, or the `*` group if none does, and ignores groups written
for other crawlers. `Crawl-delay` (in seconds) in its group slows it down.

It also reads AI-use preferences in that group: `Content-Signal: ai-train=no` (Cloudflare's
managed `robots.txt`) or `Content-Usage: train-ai=n` (IETF AI preferences) make it treat the whole
site as disallowed; with a path (`Content-Signal: /blog/ ai-train=no`), everything under that path.

It re-reads `robots.txt` at least once a day. A `4xx` response means no restriction, as RFC 9309
says; a `5xx` or an unreachable file means it fetches nothing from the site until it can read it.

## IP ranges and verification

- IP list: https://river.ai/riverbot.json, a JSON object with `creationTime` and a `prefixes`
  array of `{"ipv4Prefix": ...}` objects. On 2026-11-10 it held 100 IPv4 prefixes, all `/32`, with
  `creationTime` 2026-10-28. No IPv6. The same addresses are listed on the documentation page.
- Reverse DNS: each address resolves to a name under `.bot.river.ai` (for example
  `crawl-3-212-178-146.bot.river.ai`) that resolves back to the same address. River says a request
  claiming to be RiverBot from any other address is not from River.
- Web Bot Auth: every request is signed with HTTP Message Signatures (RFC 9421), with a
  `Signature-Agent` header of `"https://river.ai"`. The key directory,
  https://river.ai/.well-known/http-message-signatures-directory, held one `OKP` / `Ed25519` key on
  2026-11-10.
- ASN: not documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `RiverBot`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` sets the identity `River` on a forward-confirmed hostname ending with
`.bot.river.ai`, the published list (`riverbot-ips.json`, 100 prefixes, the same as the published
list on 2026-11-10) or a verified signature from `https://river.ai`, which needs the `webbotauth`
module.

## Misc

Contact and abuse reports: bot@river.ai, with the domain or network and, if possible, the time and
address of the requests. River says it stops crawling the sites it is told to leave alone.

## Sources

- https://river.ai/bot (checked 2026-11-10)
- https://river.ai/riverbot.json (checked 2026-11-10)
- https://river.ai/.well-known/http-message-signatures-directory (checked 2026-11-10)
