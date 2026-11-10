---
name: ElevenlabsBot
operator: ElevenLabs
website: https://elevenlabs.io
documentation: https://elevenlabs.io/docs/bots
category: ai-assistant
robots_txt_token: ElevenlabsBot
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: ElevenlabsBot
  identity: null
last_checked: 2026-11-10
---

# ElevenlabsBot

## Description

ElevenlabsBot fetches the pages that ElevenLabs customers add to their agents' knowledge bases,
when they add them and when they refresh them.

## Behavior

ElevenLabs says ElevenlabsBot honors `robots.txt`, and that `robots.txt` changes are reflected
within about 24 hours. How often pages are refreshed and whether JavaScript is rendered are not
documented.

## User agents

Exact strings, one per line:

```
ElevenlabsBot/1.0
```

ElevenLabs says the version number may change.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: ElevenlabsBot
Disallow: /
```

The `ElevenlabsBot` and `ElevenlabsCrawler` settings are independent: a site can allow
ElevenlabsBot, so that ElevenLabs agents can use its pages, and disallow ElevenlabsCrawler.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-11-07 and 2026-11-10, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS396982 Google LLC: `35.255.99.0/24`, `34.60.46.0/24`, `35.255.148.0/24`, `34.132.187.0/24`, `136.64.40.0/24`, `136.111.42.0/24`, `34.72.73.0/24`, `35.202.13.0/24`, and 80 more

## Hyperwatch

`@hyperwatch/useragent` returns the family `ElevenlabsBot`. `src/modules/identity.js` has no rule
for it, so Hyperwatch sets no identity.

## Misc

ElevenLabs' training crawler is [ElevenlabsCrawler](elevenlabscrawler.md).

## Sources

- https://elevenlabs.io/docs/bots (checked 2026-11-10)
