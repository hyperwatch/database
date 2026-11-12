---
name: IsonSearchBot
operator: IsonAI (PT Epithre Teknologi Indonesia)
website: https://www.isonai.com
documentation: https://search.isonai.com/bot
category: ai-search
robots_txt_token: IsonSearchBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://search.isonai.com/bot/ips.json
  hostnames: []
hyperwatch:
  family: IsonSearchBot
  identity: Ison
last_checked: 2026-11-12
---

# IsonSearchBot

## Description

IsonSearchBot builds the index behind Ison Search, "a search engine run from Indonesia", operated by
IsonAI (PT Epithre Teknologi Indonesia). It reads public pages "to build the search index and
support cited answers that link back to the original sources". IsonAI says crawled pages also
ground the cited answers of its assistant, and that content-quality classifiers filter spam from
the index.

## Behavior

IsonAI documents:

- `robots.txt` is honored per host, for the `IsonSearchBot` group or `*`: `Disallow`, `Crawl-delay`
  and `Sitemap` are read and applied. A change "takes effect the next time we read the file"; how
  often it is read is not documented.
- Rate: paced per site, starting at one request per second, speeding up only while responses stay
  fast and error-free, never above two per second or one connection at a time. Slow answers,
  timeouts and 5xx slow it down; 429 and 403 drop it to the minimum and pause. `Crawl-delay` always
  wins, up to 30 seconds.
- JavaScript: most pages are fetched as static HTML; pages that only show their text with
  JavaScript are rendered in a headless browser that sends the same user agent and follows the same
  rules.
- It submits no forms, attempts no authentication, fetches nothing behind a paywall, and never
  solves CAPTCHAs or changes its identity to get past a block.
- Scope: the public web, with Indonesian sources given priority.

## User agents

Exact strings, one per line:

```
IsonSearchBot/1.0 (+https://search.isonai.com/bot)
```

This is the documented string. IsonAI says every request, rendered pages included, carries it, and
that the robot never presents itself as a browser.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: IsonSearchBot
Disallow: /
```

For pages already indexed, IsonAI asks for an email to hello@epithre.com with the subject
`IsonSearch removal: [domain]`: removal within 24 hours, and the domain goes on a permanent
exclusion list.

## IP ranges and verification

IsonAI publishes the addresses at https://search.isonai.com/bot/ips.json: an object with
`creationTime`, `userAgent`, `documentation`, `contact`, an `undeclaredEgressNote` and a `prefixes`
array of `{"ipv4Prefix": ...}` objects. On 2026-11-12 it held 4 IPv4 prefixes, all `/32`, with
`creationTime` 2026-11-09. The list is not complete by design: one crawler node uses a shared mobile
network whose rotating address is left out, so "an address outside the list alone does not prove
impersonation". Some listed addresses are also used by IsonAI-User (see Misc). IsonAI says it does
not rely on reverse DNS because not every network it uses lets it set its own names. No hostnames
or ASN are documented.

IsonAI calls the signature "the stronger check": every request, rendered pages included, is signed
with Web Bot Auth (RFC 9421), with the `Signature-Agent` value `"https://search.isonai.com"`. The key
directory is https://search.isonai.com/.well-known/http-message-signatures-directory: on 2026-11-12
it held 1 `OKP` / `Ed25519` key without a `kid`; the directory's own signature uses the key's JWK
thumbprint as its `keyid`. IsonAI also says Cloudflare lists IsonSearchBot as a verified bot.

## Hyperwatch

`@hyperwatch/useragent` 4.1.0 returns the family `IsonSearchBot`. In Hyperwatch 5.6.0,
`src/modules/identity.js` sets the identity `Ison` signed only: a verified signature of
`https://search.isonai.com` (the `signedOnly` map, checked before the rules per family) gives `Ison`
whatever the user agent. `https://search.isonai.com` is in `src/data/webbotauth-agents.json`, so
Hyperwatch fetches its key directory. There is no rule for the family `IsonSearchBot`, and the
published list is not used: without the `webbotauth` module (off by default) or without a valid
signature, a request from a listed address gets no identity.

## Misc

- IsonAI-User, IsonAI's second agent, visits a page when a person using IsonAI asks about it; it
  does not crawl and is not used for the Ison Search index. IsonAI says `robots.txt` rules may not
  apply to it and that it can be blocked by user agent. Its user agent is
  `Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; IsonAI-User/1.0; +https://www.isonai.com/bot`,
  its addresses are at https://search.isonai.com/bot/isonai-user.json (3 IPv4 `/32` prefixes on
  2026-11-12, all also in IsonSearchBot's list, with `creationTime` 2026-11-09), and its requests
  are "generally signed" with the `Signature-Agent` `"https://www.isonai.com"`. On 2026-11-12 its key
  directory (https://www.isonai.com/.well-known/http-message-signatures-directory) answered with
  HTTP 502. Hyperwatch parses this user agent as the family `IsonAI-User` and gives it no identity.
- Contact: hello@epithre.com.

## Sources

- https://search.isonai.com/bot (checked 2026-11-12)
- https://docs.isonai.com/en/bots/ (checked 2026-11-12)
- https://search.isonai.com/bot/ips.json (checked 2026-11-12)
- https://search.isonai.com/bot/isonai-user.json (checked 2026-11-12)
- https://search.isonai.com/.well-known/http-message-signatures-directory (checked 2026-11-12)
- https://www.isonai.com/.well-known/http-message-signatures-directory (checked 2026-11-12)
