---
name: Sogou web spider
operator: Sogou
website: https://www.sogou.com
documentation: https://www.sogou.com/docs/help/webmasters.htm
category: search-engine
robots_txt_token: Sogou web spider
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Sogou web spider
  identity: Sogou
last_checked: 2026-10-15
---

# Sogou web spider

## Description

Sogou web spider is the crawler of Sogou, the Chinese search engine. It fetches pages, stores them
and follows their links so they can be found in Sogou search. This file also covers
`Sogou Pic Spider`, which Hyperwatch groups with it.

## Behavior

Sogou says the spider opens only one connection to a given server address, with a few seconds
between fetches. A page is refreshed a few days after it was indexed at the earliest, then on a
schedule based on its importance and history of changes. It discards pages deep in a site's link
structure and pages behind many redirects, and prefers static pages to dynamic ones.

A new `robots.txt` can take several weeks to take effect. `Crawl-delay` support and JavaScript
rendering are not documented.

## User agents

Sogou's page gives no user agent string. According to Known Agents, the spider sends:

```
Sogou web spider/4.0(+http://www.sogou.com/docs/help/webmasters.htm#07)
```

No source with a full `Sogou Pic Spider` string was found.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Sogou says the spider supports `robots.txt` and refers to http://www.robotstxt.org/ for the rules.
It does not name the token to use. According to Known Agents:

```
User-agent: Sogou web spider
Disallow: /
```

## IP ranges and verification

None published. Sogou documents no reverse DNS hostnames, IP list or ASN.

## Hyperwatch

`@hyperwatch/useragent` parses the Known Agents string as family `Sogou web spider`.
`src/modules/identity.js` sets the identity `Sogou` for the families `Sogou web spider` and
`Sogou Pic Spider` when the unconfirmed hostname ends with `.sogou.com`. A fallback also sets
`Sogou` for any request, whatever its user agent, whose unconfirmed hostname ends with
`.crawl.sogou.com`. Sogou does not document either suffix, so neither check comes from the operator,
and neither is forward-confirmed.

## Misc

Sogou may refuse to index sites it considers spam, low quality or illegal.

## Sources

- https://www.sogou.com/docs/help/webmasters.htm (checked 2026-10-15)
- https://knownagents.com/agents/sogou-web-spider (checked 2026-10-15)
