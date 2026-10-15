---
name: AmberAI-SourceReader
operator: Unknown
website: null
documentation: null
category: unknown
robots_txt_token: AmberAI-SourceReader
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: AmberAI-SourceReader
  identity: null
last_checked: 2026-10-15
---

# AmberAI-SourceReader

## Description

AmberAI-SourceReader is a robot whose user agent carries no URL or contact. No public page describes
it, and nothing reliable identifies its operator. The name suggests a tool that reads source pages
for an AI product called "AmberAI", but this is not confirmed.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
AmberAI-SourceReader/1.0
```

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: AmberAI-SourceReader
Disallow: /
```

The token is the product name in the user agent. Whether the robot reads `robots.txt` is not
documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `AmberAI-SourceReader`. `src/modules/identity.js` has no
rule for it, so it gets no identity.

## Misc

- "amberAI" is the name of the AI assistant in amberSearch (now amber, amber.de), a German
  enterprise search product that cites the sources of its answers. No amber page mentions this user
  agent, so the link is not established.

## Sources

- https://helpcenter.ambersearch.de/articles/23425544388637-new-improved-referencing-through-amberai (checked 2026-10-15)
- https://amber.de/ (checked 2026-10-15)
