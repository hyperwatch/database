---
name: ShapBot
operator: Parallel Web Systems
website: https://parallel.ai
documentation: https://parallel.ai/parallel-web-systems-bots
category: ai-search
robots_txt_token: ShapBot
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://docs.parallel.ai/resources/shapbot.json
  hostnames: []
hyperwatch:
  family: ShapBot
  identity: Parallel
last_checked: 2026-10-15
---

# ShapBot

## Description

ShapBot is the crawler of Parallel Web Systems, which sells web search and extraction APIs for AI
agents. Parallel says ShapBot "collects publicly available web content to build and maintain
Parallel's search index". Restricting it "may reduce your site's visibility and discoverability
through Parallel's web APIs and search features".

## Behavior

Parallel says webmasters "can manage automated access using robots.txt with the User-agent: ShapBot
directive". Crawl rate, `Crawl-delay` support, JavaScript rendering and `robots.txt` caching are not
documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; ShapBot/0.1.0
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: ShapBot
Disallow: /
```

Parallel's other agent, Shap-User, accesses content on behalf of users and "is intended to provide
visibility rather than to be managed through automated controls": Parallel points to ShapBot for
controlling automated crawling.

## IP ranges and verification

Parallel publishes the addresses at https://docs.parallel.ai/resources/shapbot.json: an object with
`creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` objects. On 2026-10-15 it held 10
IPv4 prefixes, all `/32`, with `creationTime` 2026-07-14. No reverse DNS hostname or ASN is
documented. A reverse lookup of three listed addresses on 2026-10-15 returned
`*.bc.googleusercontent.com` names, a Google Cloud suffix shared by all its customers.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ShapBot`. In Hyperwatch `main` (after 5.3.3),
`src/modules/identity.js` sets the identity `Parallel` on a cloud hostname ending with
`.googleusercontent.com` or the published list (`shapbot-ips.json`). The cloud hostname is not
documented by Parallel, and any Google Cloud customer passes it.

## Misc

- Shap-User: `Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; Shap-User/0.1.0`.
  Parallel says it "is not used for crawling the web in an automatic fashion". No list is published
  for it. Hyperwatch parses it as the family `Shap-User` and gives it no identity.
- Parallel's contacts: support@parallel.ai for crawler issues, index@parallel.ai for content
  questions.

## Sources

- https://parallel.ai/parallel-web-systems-bots (checked 2026-10-15)
- https://docs.parallel.ai/resources/crawler (checked 2026-10-15)
- https://docs.parallel.ai/resources/shapbot.json (checked 2026-10-15)
