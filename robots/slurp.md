---
name: Yahoo! Slurp
operator: Yahoo
website: https://search.yahoo.com
documentation: https://help.yahoo.com/kb/SLN22600.html
category: search-engine
robots_txt_token: Slurp
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Yahoo! Slurp
  identity: Yahoo
last_checked: 2026-10-15
---

# Yahoo! Slurp

## Description

Slurp is the Yahoo Search robot that crawls and indexes web pages. Yahoo says some Yahoo Search
results come from partners (Bing's crawler), but sites should allow Slurp to appear in Yahoo Mobile
Search results. Slurp also collects content from partner sites for Yahoo News, Yahoo Finance and
Yahoo Sports, and fetches pages "to confirm accuracy and improve Yahoo's personalized content".

## Behavior

Yahoo says Slurp "is designed to make reasonable requests that don't overburden websites" and
supports `Crawl-delay`. JavaScript rendering and `robots.txt` caching are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; Yahoo! Slurp; http://help.yahoo.com/help/us/ysearch/slurp)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Slurp
Disallow: /
```

Slurp obeys the first record whose `User-agent` contains `Slurp`; if there is none, the first
`User-agent: *` record. `Crawl-delay` is supported. Problems can be reported to
crawl-support@yahooinc.com.

## IP ranges and verification

None published. Yahoo's current pages give no IP list and no reverse DNS names.

According to a 2007 Search Engine Journal article relaying Yahoo's announcement, Slurp then moved
to the domain `crawl.yahoo.net`: the reverse DNS name of every Yahoo Search crawler ends with
`crawl.yahoo.net`, and it must resolve back to the same address. No current Yahoo page confirms
this.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Yahoo! Slurp`. In Hyperwatch `main` (after 5.3.3),
`src/modules/identity.js` sets the identity `Yahoo` for the families `Yahoo` and `Yahoo! Slurp` when
the unconfirmed hostname ends with `.crawl.yahoo.net`. The 2007 instructions describe a
forward-confirmed check; the rule does not use the confirmed hostname. No current Yahoo page
documents the suffix.

## Misc

- Yahoo's guide to meta tags and `robots.txt`
  (https://help.yahoo.com/kb/guide-meta-tags-robotstxt-slurp-sln2213.html) now only says that
  Yahoo Search results come from Slurp and Bing's crawler, and points to Bing's documentation.
- YahooMailProxy, Yahoo Mail's image fetcher, is a separate robot. Hyperwatch gives it the same
  identity name, `Yahoo`.

## Sources

- https://help.yahoo.com/kb/SLN22600.html (checked 2026-10-15)
- https://help.yahoo.com/kb/guide-meta-tags-robotstxt-slurp-sln2213.html (checked 2026-10-15)
- https://www.searchenginejournal.com/yahoo-searchs-slurp-crawler-updates-moves-to-new-address/5049/ (2007, checked 2026-10-15)
