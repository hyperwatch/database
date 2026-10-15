---
name: JerryOSINT
operator: unknown
website: null
documentation: null
category: research
robots_txt_token: JerryOSINT
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: JerryOSINT
  identity: null
last_checked: 2026-10-15
---

# JerryOSINT

## Description

JerryOSINT is an unidentified robot. Its user agent describes it as "personal open-source
research" (OSINT, open-source intelligence). No operator, website or documentation could be found.

## Behavior

Not documented. The user agent claims "respects robots.txt"; there is no other statement to check
it against.

## User agents

```
Mozilla/5.0 (compatible; JerryOSINT/1.0; personal open-source research; respects robots.txt)
```

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: JerryOSINT
Disallow: /
```

The token is not documented. `JerryOSINT` is the product name in the user agent.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `JerryOSINT`. `src/modules/identity.js` has
no rule for it, so it gets no identity.

## Misc

A web search for the name found no page about it.

## Sources

- Web search for "JerryOSINT" (no relevant result) (checked 2026-10-15)
