---
name: IbouBot
operator: ibou
website: https://www.ibou.com
documentation: https://www.ibou.com/iboubot.html
category: search-engine
robots_txt_token: IbouBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://www.ibou.com/iboubot-ip-ranges.json
  hostnames:
    - ibou.io
hyperwatch:
  family: www.ibou.com
  identity: null
last_checked: 2026-10-16
---

# IbouBot

## Description

IbouBot is a crawler of ibou, a French search engine. ibou says it "discovers publicly accessible
pages and indexes them for our search engine", and that it does not train AI models with the data.

## Behavior

- Crawl rate: 5 seconds between two requests to the same host, and 2.5 seconds between requests to
  the same IP for the same domain. ibou gives about 0.4 requests per second per domain (about 24
  per minute) as the worst case.
- `Crawl-delay` is supported, per host: a server hosting several domains gets the rates above.
- It follows `robots.txt` and its `Disallow` directives.
- It keeps fetching pages that redirect (301) or are missing (404), and follows `nofollow` links.
- JavaScript rendering is not documented. How often `robots.txt` is re-read is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; IbouBot/1.0; +bot@ibou.com; +https://www.ibou.com/iboubot.html)
```

An older form, `Mozilla/5.0 (compatible; IbouBot/1.0; +bot@ibou.io; +https://ibou.io/iboubot.html)`,
appears in `@hyperwatch/useragent`'s samples; `https://ibou.io/iboubot.html` now redirects to the
page above.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: IbouBot
Disallow: /
```

To slow it down instead:

```
User-agent: IbouBot
Crawl-Delay: 10
```

## IP ranges and verification

- IP list: https://www.ibou.com/iboubot-ip-ranges.json. JSON object with `creationTime` and a
  `prefixes` array of `{"ipv4Prefix": ...}` objects. On the check date it held one prefix,
  `217.113.196.0/24`, with `creationTime` 2025-07-25. ibou says the list may change and should be
  fetched periodically.
- Reverse DNS: forward-confirmed names under `ibou.io`, for example `c001.ibou.io` for
  `217.113.196.1`.
- ASN: not documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `www.ibou.com` for the current string and `ibou.io` for
the older one: the contact address between the version and the URL makes it fall back to the URL's
host. In Hyperwatch `main` (after 5.3.3), `src/modules/identity.js` sets the identity `ibou` for the
family `IbouBot` on a forward-confirmed hostname ending with `.ibou.io` or the published list
(`iboubot-ips.json`, 1 prefix). Until the parser returns `IbouBot` (fixed in `@hyperwatch/useragent`
[#227](https://github.com/hyperwatch/useragent/pull/227), not released), that rule never matches
and IbouBot gets no identity.

## Misc

- ibou documents a second crawler, `ibou-search`, with its own page, user agent and IP list: see
  [ibou-search](ibou-search.md).
- Cloudflare lists IbouBot as a Verified Bot in the "Search" category, according to ibou.
- Contact: `bot@ibou.com`.

## Sources

- https://www.ibou.com/iboubot.html (checked 2026-10-16)
- https://www.ibou.com/iboubot-ip-ranges.json (checked 2026-10-16)
