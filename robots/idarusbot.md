---
name: IdarusBot
operator: Idarus
website: https://search.magical.rocks
documentation: https://search.magical.rocks/bot
category: search-engine
robots_txt_token: IdarusBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://search.magical.rocks/bot
  hostnames: []
hyperwatch:
  family: IdarusBot
  identity: null
last_checked: 2026-10-15
---

# IdarusBot

## Description

IdarusBot is the crawler of Idarus, a small independent search engine. Idarus describes itself as
the relaunch of a hobby search engine that ran from 2009 to 2012. The crawler visits public web
pages so they can appear in Idarus search results. The text of some pages may also be kept in a
collection used to train language models, with separate opt-outs (see below).

## Behavior

- `robots.txt`: followed, including `Crawl-delay`. It is read before the first request of every
  crawl run.
- Rate: at most one request at a time per site, with a pause of about one second after each
  response, longer if `Crawl-delay` asks for it. Sites on the same server share this budget.
- On `429` or `503`, it waits for the time given in `Retry-After` (at least 10 seconds, 60 by
  default).
- It only requests public pages over HTTP and HTTPS on standard ports. It never logs in, submits
  forms or scans ports.
- Discovery: through links, and through public Certificate Transparency logs.
- It stores page text, title, description and links. Pages are revisited at most about once a
  week.
- It may request `/.well-known/tdmrep.json` once a day per site.
- JavaScript rendering: not documented. The crawler is written in Rust.

## User agents

Exact strings, one per line:

```
IdarusBot/2.0 (+https://idarus.de/bot)
IdarusBot/2.0 (+https://search.magical.rocks/bot)
```

The documented string is `IdarusBot/2.0 (+https://search.magical.rocks/bot)`. The host `idarus.de`
did not resolve in DNS on 2026-10-15.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages). Hyperwatch does not verify this robot, so other clients using its name may be included.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: IdarusBot
Disallow: /
```

To slow it down:

```
User-agent: IdarusBot
Crawl-delay: 10
```

Training text has its own opt-outs. A page is left out of the training collection if any of these
apply:

- `robots.txt` rules for `IdarusBot-Training` (separate from search):

  ```
  User-agent: IdarusBot-Training
  Disallow: /
  ```

- `robots.txt` rules for other AI training crawlers (such as `GPTBot`, `CCBot`,
  `Google-Extended`), which IdarusBot applies to itself.
- A TDM reservation (W3C TDMRep): the `tdm-reservation: 1` HTTP header, the
  `<meta name="tdm-reservation" content="1">` tag or `/.well-known/tdmrep.json`.
- `noai` in an `X-Robots-Tag` header or robots meta tag, or `noindex` anywhere.
- Paywalls, login walls, and pages the search index treats as spam.

## IP ranges and verification

The bot page states that genuine requests come only from `141.94.42.166`. This address is in a
network announced by AS16276 (OVH), with the PTR `vps-fe3a6202.vps.ovh.net`. No reverse DNS method
is documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Reverse DNS hostnames:

- `*.vps.ovh.net` (forward-confirmed, addresses in the published ranges)

## Hyperwatch

`@hyperwatch/useragent` returns the family `IdarusBot`. `src/modules/identity.js` has no rule for
it, so it gets no identity.

## Misc

The site's imprint says legal details will be added before the site goes public. A contact
address for the crawler is not yet published.

## Sources

- https://search.magical.rocks/bot (checked 2026-10-15)
- https://search.magical.rocks/about (checked 2026-10-15)
- https://search.magical.rocks/imprint (checked 2026-10-15)
- RADb route objects for 141.94.0.0/16, `whois -h whois.radb.net` (checked 2026-10-15)
