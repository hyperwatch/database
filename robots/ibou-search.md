---
name: ibou-search
operator: ibou
website: https://www.ibou.com
documentation: https://www.ibou.com/crawlers.html
category: search-engine
robots_txt_token: ibou-search
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://www.ibou.com/ibousearch-ip-ranges.json
  hostnames:
    - ibou.io
hyperwatch:
  family: ibou-search
  identity: ibou
last_checked: 2026-11-12
---

# ibou-search

## Description

ibou-search is the crawler of ibou, a French search engine. It "discovers publicly accessible pages
and indexes them for our search engine". ibou states that it does not train AI models with the
data.

## Behavior

- Crawl rate: 5 seconds between two requests to the same host, and 2.5 seconds between requests to
  the same IP for the same domain. ibou gives about 0.4 requests per second per domain (about 24
  per minute) as the worst case.
- `Crawl-delay` is supported, per host.
- It follows `robots.txt`.
- JavaScript rendering is not documented. How often `robots.txt` is re-read is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; ibou-search/2.0; +https://ibou.com/crawlers.html)
```

ibou documents `Mozilla/5.0 (compatible; ibou-search/2.0; +https://www.ibou.com/crawlers.html)`,
with `www.` in the URL. Its technical table gives the version as 1.0 while the user agent says 2.0.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages). Hyperwatch did not verify this robot then, so other clients using its name may be included.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html;q=0.95,text/*;q=0.9,*/*;q=0.8` (100%) |
| `from` | `network-abuse@ibou.com` (100%) |
| `signature` | `(present)` (100%) |
| `signature-agent` | `https://ibou.io` (100%) |
| `signature-input` | `(present)` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: ibou-search
Disallow: /
```

To slow it down instead:

```
User-agent: ibou-search
Crawl-Delay: 10
```

## IP ranges and verification

- IP list: https://www.ibou.com/ibousearch-ip-ranges.json. JSON object with `creationTime` and a
  `prefixes` array whose objects carry `ipv4Prefix` and `ipv6Prefix` keys. On 2026-11-10 it held
  three prefixes: `188.241.38.0/24`, `217.113.196.0/24` and `2a0e:6240:e000::/44`, with
  `creationTime` 2026-11-04 (on 2026-10-15, the first and the last, dated 2026-09-28). ibou says
  the list may change and should be fetched periodically.
- Reverse DNS: forward-confirmed names under `ibou.io`, for example `c40037.ibou.io`.
- Web Bot Auth: ibou's page doesn't mention it, but the requests above are signed, with
  `Signature-Agent` set to the bare URL `https://ibou.io` (not a quoted string or a dictionary).
  The key directory, https://ibou.io/.well-known/http-message-signatures-directory, held one `OKP`
  / `Ed25519` key on 2026-11-12, with its JWK thumbprint as `kid` (a signature's `keyid` finds it
  either way).
- ASN: not documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ibou-search`. In Hyperwatch 5.6.0,
`src/modules/identity.js` sets the identity `ibou` on a forward-confirmed hostname ending with
`.ibou.io`, a verified signature of `https://ibou.io` (needs the `webbotauth` module, off by
default; since 5.6.0 it accepts a bare-URL `Signature-Agent` like ibou's), then the published list
(`ibou-ips.json`, the same 3 prefixes). The same signature also gives Barkrowler the identity
`Babbar`. IbouBot has its own rule and list (see [IbouBot](iboubot.md)).

## Misc

- ibou documents a second crawler, `IbouBot`, with its own page, user agent and IP list: see
  [IbouBot](iboubot.md).
- Cloudflare classifies ibou-search as a search crawler, according to ibou.

## Sources

- https://www.ibou.com/crawlers.html (checked 2026-10-15)
- https://www.ibou.com/ibousearch-ip-ranges.json (checked 2026-11-10)
- https://ibou.io/.well-known/http-message-signatures-directory (checked 2026-11-12)
