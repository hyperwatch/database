---
name: alexa site audit
operator: Alexa Internet (Amazon); service shut down
website: https://www.alexa.com
documentation: null
category: seo
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: alexa site audit
  identity: Alexa
last_checked: 2026-10-15
---

# alexa site audit

## Description

`alexa site audit` was the crawler of the Site Audit feature of Alexa.com, the web traffic
ranking service of Alexa Internet, an Amazon company. Amazon retired Alexa.com on 2022-05-01:
Engadget reported on 2021-12-09 that Amazon was "retiring Alexa.com on May 1st, 2022". On
2026-10-15, `https://www.alexa.com/` redirected to `https://alexa.amazon.com/`, the page of
Amazon's voice assistant, with no trace of the ranking service. The crawler should no longer run:
requests with this user agent today come from someone else.

## Behavior

Not documented: the help page linked from the user agent no longer exists.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; alexa site audit/1.0; +http://www.alexa.com/help/webmasters; )
```

This string comes from the crawler-user-agents list. The URL it gives now redirects to
`https://alexa.amazon.com/`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

No token was ever documented in a source that can still be fetched. Since the service is shut
down, there is nothing to block with `robots.txt`.

## IP ranges and verification

None published. No IP list or reverse DNS names can be found for the former service.

## Hyperwatch

`@hyperwatch/useragent` returns the family `alexa site audit`. `src/modules/identity.js` sets the
identity `Alexa` when the unconfirmed hostname ends with `.alexa.com`: whoever controls the
reverse DNS of an address can set it. No documentation of that suffix was found. As Alexa.com is
shut down, the rule should no longer match legitimate traffic.

## Misc

Matomo's device-detector lists `alexa site
audit` as a "Site Monitor" produced by Alexa Internet.

## Sources

- https://www.engadget.com/amazon-shutting-down-alexa-web-ranking-site-110319891.html (checked 2026-10-15)
- https://www.alexa.com/ (redirects to https://alexa.amazon.com/, checked 2026-10-15)
- https://raw.githubusercontent.com/monperrus/crawler-user-agents/master/crawler-user-agents.json (checked 2026-10-15)
- https://raw.githubusercontent.com/matomo-org/device-detector/master/regexes/bots.yml (checked 2026-10-15)
