---
name: RavenCrawler
operator: Raven Tools (TapClicks, Inc.)
website: https://raventools.com
documentation: null
category: seo
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: RavenCrawler
  identity: null
last_checked: 2026-10-15
---

# RavenCrawler

## Description

RavenCrawler is the crawler of Raven Tools' Site Auditor, an SEO audit tool. The Raven Tools
website is run by TapClicks, Inc. (its footer reads "© 2007-2026 TapClicks, Inc."). Raven
publishes no page about the crawler itself.

## Behavior

The Site Auditor page says a user chooses a crawl depth of 1 to 10,000 pages, can exclude pages
from the crawl, and can schedule audits weekly or monthly. It lists "robots.txt issues" among
the problems the audit reports, but does not say how the crawler itself treats `robots.txt`.

Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; RavenCrawler/2.0; +https://raventools.com/seo-website-auditor/)
```

Raven does not publish its user agent. This string comes from the crawler-user-agents list and
links to the Site Auditor page (the URL now redirects to `https://raventools.com/site-auditor/`).
Matomo's device-detector also lists a `RavenCrawler` pattern and names TapClicks, Inc. as its
producer.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: RavenCrawler
Disallow: /
```

This uses the name in the user agent. Raven does not document a `robots.txt` token or whether the
crawler obeys `robots.txt`.

## IP ranges and verification

None published. No IP list, reverse DNS names or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `RavenCrawler` for the string above.
`src/modules/identity.js` has no rule for `RavenCrawler`, so Hyperwatch sets no identity for it.

It has a rule for a family named `Raven`: the identity `Raven` is set when the unconfirmed
hostname ends with `.compute-1.amazonaws.com`. This is a cloud hostname: any customer of
Amazon EC2 in us-east-1 passes. No user agent documented for Raven Tools parses as `Raven`
(a string such as `Mozilla/5.0 (compatible; Raven/1.0)` would), so this rule does not cover
RavenCrawler, and nothing published by Raven supports the EC2 hostname.

## Misc

According to Known Agents, RavenCrawler "analyzes websites as part of their SEO website auditing
service". Centinel Analytica says Raven publishes nothing to check a request's source against.

## Sources

- https://raventools.com/site-auditor/ (checked 2026-10-15)
- https://raw.githubusercontent.com/monperrus/crawler-user-agents/master/crawler-user-agents.json (checked 2026-10-15)
- https://raw.githubusercontent.com/matomo-org/device-detector/master/regexes/bots.yml (checked 2026-10-15)
- https://knownagents.com/operators/raven (checked 2026-10-15)
- https://docs.centinelanalytica.com/crawlers/raven (search result summary, 2026-10-15)
