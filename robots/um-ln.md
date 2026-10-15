---
name: um-LN
operator: Ubermetrics Technologies
website: https://www.ubermetrics-technologies.com
documentation: null
category: marketing
robots_txt_token: um-LN
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Ubermetrics
  identity: Ubermetrics
last_checked: 2026-10-15
---

# um-LN

## Description

um-LN names Ubermetrics Technologies in its user agent. Ubermetrics describes itself as
"AI-Powered Content Intelligence for Digital Communicators". Its website has no page about the
crawler. According to Known Agents, Ubermetrics is the research and development center of the
UNICEPTA Group, and the crawler "collects web content to support AI-based solutions for
decision-makers in communication, marketing, and strategic business areas".

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; um-LN/1.0; https://www.ubermetrics-technologies.com/; Windows NT 6.1; WOW64; rv:125.0) Gecko/20100101 Firefox/125.1
```

This string comes from Known Agents. Ubermetrics does not publish it.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: um-LN
Disallow: /
```

The token is taken from the user agent. Whether the robot obeys `robots.txt` is not documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` maps `um-LN` to the family `Ubermetrics`. Hyperwatch sets the identity
`Ubermetrics` when the reverse DNS name ends with `.your-server.de`. This is a cloud hostname: any
Hetzner customer passes it. The hostname is also not confirmed by a forward lookup. Ubermetrics
does not document running on Hetzner.

## Misc

Nothing else documented.

## Sources

- https://www.ubermetrics-technologies.com/ (checked 2026-10-15, no crawler page found)
- https://knownagents.com/agents/um-ln (checked 2026-10-15)
