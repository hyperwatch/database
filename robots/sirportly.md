---
name: Sirportly t.co expander
operator: Krystal Hosting Ltd (Sirportly)
website: https://sirportly.com
documentation: null
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Sirportly t.co expander
  identity: Sirportly
last_checked: 2026-10-15
---

# Sirportly t.co expander

## Description

Sirportly is a help desk application. Its site says it brings together messages from social
networks and email, and that it is "a Krystal Labs product" of Krystal Hosting Ltd. The user agent
name suggests a component that follows `t.co` short links (X, formerly Twitter) to their
destination, but Sirportly does not document it.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
Sirportly t.co expander
```

This is the name Hyperwatch's parser returns for this string. Sirportly does not document it.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

No token is documented, and whether it reads `robots.txt` is not documented.

## IP ranges and verification

None published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Sirportly t.co expander`. `src/modules/identity.js`
sets the identity `Sirportly` when the reverse DNS hostname ends with `.labs.k.io`. This reads the
unconfirmed hostname, and the suffix is not documented by Sirportly. On 2026-10-15 `k.io` and
`labs.k.io` redirected to krystal.io.

## Misc

Searched on 2026-10-15: sirportly.com, its documentation pages, and web searches for the user agent,
which found nothing about it.

## Sources

- https://sirportly.com (checked 2026-10-15)
- https://sirportly.com/docs (checked 2026-10-15)
