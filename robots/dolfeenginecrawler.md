---
name: DolfeEngineCrawler
operator: Unknown
website: null
documentation: null
category: unknown
robots_txt_token: DolfeEngineCrawler
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: null
  identity: Dolfe
last_checked: 2026-10-15
---

# DolfeEngineCrawler

## Description

No documentation was found for this robot. Web searches for `DolfeEngineCrawler` returned nothing
about it, and the Known Agents, Dark Visitors and CrawlConsole directories have no entry for it.
`dolfe.com` is a parked domain for sale. `dolfe.ai` is an unrelated Taiwanese lifestyle site. Its
operator and purpose are unknown.

## Behavior

Not documented.

## User agents

No user agent string was found in any source. The name `DolfeEngineCrawler` comes from the
Hyperwatch identity rule.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: DolfeEngineCrawler
Disallow: /
```

The token is assumed from the robot's name. Whether the robot obeys `robots.txt` is not documented.

## IP ranges and verification

None published.

## Hyperwatch

No user agent string was available to parse, so the agent family is not confirmed. The rule in
`src/modules/identity.js` applies to the family `DolfeEngineCrawler`: it sets the identity `Dolfe`
when the reverse DNS name ends with `.googleusercontent.com`. This is a cloud hostname: any Google
Cloud customer passes it. The hostname is also not confirmed by a forward lookup. Nothing from an
operator supports the check.

## Misc

Nothing else documented.

## Sources

- https://dolfe.com/ (checked 2026-10-15, parked domain)
- https://dolfe.ai/ (checked 2026-10-15, unrelated)
- https://knownagents.com/agents/dolfeenginecrawler (checked 2026-10-15, returns 404)
- https://darkvisitors.com/agents/dolfeenginecrawler (checked 2026-10-15, returns 404)
- https://crawlconsole.com/web-crawlers/dolfeenginecrawler (checked 2026-10-15, returns 404)
