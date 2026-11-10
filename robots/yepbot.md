---
name: YepBot
operator: Ahrefs (Yep)
website: https://yep.com
documentation: https://yep.com/yepbot/
category: search-engine
robots_txt_token: YepBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://api.ahrefs.com/v3/public/crawler-ip-ranges
  hostnames:
    - "*.ahrefs.com"
hyperwatch:
  family: YepBot
  identity: Ahrefs
last_checked: 2026-11-10
---

# YepBot

## Description

YepBot is a crawler of Ahrefs. With [AhrefsBot](ahrefsbot.md), it builds the index of web pages used
by Yep, Ahrefs' web search engine, and by Ahrefs' SEO toolset. AhrefsBot remains the main source of
data for both.

yep.com/yepbot/ answered `403` to automated fetches on 2026-11-10. What is said here comes from that
page as shown in search results the same day, and should be checked against the page itself.

## Behavior

YepBot respects `robots.txt` `Disallow` and `Allow` rules and supports `Crawl-delay` in seconds. It
may take some time to pick up a change to `robots.txt`. Crawl rate and JavaScript rendering are not
documented in what could be read.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; YepBot/1.0; +http://yep.com/yepbot/)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet. The requests seen with its user
agent fail the documented checks (see "Observed" below).

## Blocking with robots.txt

```
User-agent: YepBot
Disallow: /
```

## IP ranges and verification

The page gives a reverse DNS suffix of `ahrefs.com` and links to a "current list" of IP ranges.
Which list was not readable; Ahrefs' crawler list, https://api.ahrefs.com/v3/public/crawler-ip-ranges
(see [AhrefsBot](ahrefsbot.md)), held 81 IPv4 prefixes on 2026-11-10.

### Observed

Requests with this user agent seen between 2026-11-07 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from:

- AS14618 Amazon.com, Inc.: `32.192.171.0/24`, `52.203.170.0/24`

Neither address is in Ahrefs' list, and both have `*.compute-1.amazonaws.com` reverse DNS names,
not `ahrefs.com`: these requests do not pass the documented checks.

## Hyperwatch

`@hyperwatch/useragent` returns the family `YepBot`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` gives it the `Ahrefs` rule, shared with `AhrefsBot` and `AhrefsSiteAudit`:
the identity `Ahrefs` on a forward-confirmed hostname ending with `.ahrefs.com`, Ahrefs' published
list (`ahrefs-ips.json`) or a verified signature of `https://ahrefs.com` (needs the `webbotauth`
module, off by default). The first two follow Yep's documentation, which doesn't mention signatures.
The requests observed above fail the hostname and list checks, so they would still get no identity.

## Misc

Nothing else documented.

## Sources

- https://yep.com/yepbot/ (checked 2026-11-10: `403` to automated fetches; content from search results)
- https://api.ahrefs.com/v3/public/crawler-ip-ranges (checked 2026-11-10)
