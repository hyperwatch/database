---
name: SeekportBot
operator: SISTRIX
website: https://www.seekport.com
documentation: https://bot.seekport.com/
category: search-engine
robots_txt_token: SeekportBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://bot.seekport.com/seekportbot_ips.txt
  hostnames: []
hyperwatch:
  family: SeekportBot
  identity: Seekport
last_checked: 2026-10-15
---

# SeekportBot

## Description

SeekportBot is the crawler of Seekport, a search engine founded in 2003 and operated since
December 2014 by SISTRIX, from Bonn (Germany). It crawls the public web to find and update content
for Seekport's own index.

## Behavior

Seekport says the bot "tries at all times not to overload websites and to make as few calls per
second as possible", obeys `Disallow` in `robots.txt` and supports `Crawl-delay`. A `robots.txt`
change "may take a while" to be registered. JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; SeekportBot; +https://bot.seekport.com)
```

Seekport says the bot "always identifies itself correctly" with this string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SeekportBot
Disallow: /
```

`Crawl-delay` sets the wait between two requests, for example `Crawl-delay: 2`. Questions go to
seekportbot@sistrix.com.

## IP ranges and verification

Seekport publishes a "complete and up-to-date list" of the addresses in use at
https://bot.seekport.com/seekportbot_ips.txt: plain text, one IPv4 address per line, no date. On
2026-10-15 it held 511 addresses, spread over several hosting providers. No reverse DNS names or
ASN are documented.

On 2026-10-15, reverse DNS lookups on 20 addresses of the list returned names ending with
`.007ac9.net` for 15 of them (`*.links.ls.007ac9.net`, `*.oi.tb.007ac9.net`), all confirmed by a
forward lookup, and no name for the other 5. Seekport does not document this domain.

## Hyperwatch

`@hyperwatch/useragent` returns the family `SeekportBot`. `src/modules/identity.js` sets the
identity `Seekport` when the unconfirmed hostname ends with `.007ac9.net`, a suffix Seekport does
not document and that some listed addresses don't have. The published IP list is not used.

The rule also covers the family `Seekport Crawler` (for example
`Mozilla/5.0 (compatible; Seekport Crawler; http://seekport.com/)`) with a cloud hostname: any
unconfirmed hostname ending with `.clients.your-server.de` (any Hetzner customer) passes. Seekport's
current page does not mention that user agent.

## Misc

Seekport describes itself as a "public, free and independent alternative to Google" that stores no
user data and shows no advertising.

## Sources

- https://bot.seekport.com/ (checked 2026-10-15)
- https://bot.seekport.com/seekportbot_ips.txt (checked 2026-10-15)
