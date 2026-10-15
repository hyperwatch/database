---
name: BLEXBot
operator: WebMeUp
website: http://webmeup-crawler.com
documentation: http://webmeup-crawler.com
category: seo
robots_txt_token: BLEXBot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames: [".webmeup.com"]
hyperwatch:
  family: BLEXBot
  identity: WebMeUp
last_checked: 2026-10-15
---

# BLEXBot

## Description

BLEXBot is a link crawler run by WebMeUp. It collects the links found on pages, for tools that
show internet marketers how sites link to each other.

The operator's page could not be read live on 2026-10-15: `http://webmeup-crawler.com/` (the URL
in the user agent) redirects to the home page of link-assistant.com, which says nothing about the
crawler, and the `https` version fails with a TLS error. `http://webmeup.com/` redirects to a
backlink checker page on the same site. Everything below comes from the Internet Archive's copy
of `http://webmeup-crawler.com/` captured on 2020-12-31 (page dated "Copyright © 2014 WebMeUp").

## Behavior

According to the archived page, BLEXBot makes at most one request every 3 seconds, or fewer if a
`Crawl-delay` is set, and backs off when a site is down or slow. It only collects links: no text
or media. It visits a page when its links have never been collected or need a refresh, so it
does not request the same page repeatedly. After a change to `robots.txt`, it should stop within
10 minutes.

JavaScript rendering is not documented.

## User agents

Exact strings, one per line (from the archived page):

```
Mozilla/5.0 (compatible; BLEXBot/1.0; +http://webmeup-crawler.com/)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: BLEXBot
Disallow: /
```

To slow it down instead:

```
User-agent: BLEXBot
Crawl-delay: 10
```

## IP ranges and verification

No IP list is published. According to the archived page, the reverse DNS name of the address
should be a subdomain of `webmeup.com`. It does not mention a forward lookup. No ASN is
documented. Whether this is still true could not be checked on the live site.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `BLEXBot`. Hyperwatch sets the identity
`WebMeUp` when the unconfirmed hostname ends with `.webmeup.com` (the same rule as
[AwarioBot](awariobot.md)). The name is not confirmed by a forward lookup.

## Misc

https://help.seranking.com/en/blex-crawler redirects to an SE Ranking knowledge base article
titled "BLEXBot Crawler", which returned "The page you were looking for doesn't exist" on
2026-10-15. SE Ranking's own link crawler is
[SERankingBacklinksBot](serankingbacklinksbot.md).

Problems were to be reported to the customer care address given on the archived page.

## Sources

- http://webmeup-crawler.com/ (checked 2026-10-15: redirects to https://www.link-assistant.com)
- https://web.archive.org/web/20201231054246/http://webmeup-crawler.com/ (checked 2026-10-15)
- https://help.seranking.com/en/blex-crawler (checked 2026-10-15: page not found)
