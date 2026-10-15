---
name: Cliqzbot
operator: Cliqz GmbH (shut down in 2020)
website: https://cliqz.com
documentation: http://cliqz.com/company/cliqzbot
category: search-engine
robots_txt_token: Cliqzbot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Cliqzbot
  identity: Cliqz
last_checked: 2026-10-15
---

# Cliqzbot

## Description

Cliqzbot was the crawler of Cliqz, a German company that built its own search engine and a
privacy-focused browser. Cliqz says on its site that "Cliqz Search shut down in 2020": its farewell
letter says the end was announced on April 29, 2020.

## Behavior

Not documented: the robot's documentation page no longer exists.

## User agents

The documentation page no longer exists, so no documented string is available. The URL in the user
agent known to Hyperwatch is `http://cliqz.com/company/cliqzbot`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Cliqzbot
Disallow: /
```

The token is the robot's name; whether it obeyed `robots.txt` is no longer documented.

## IP ranges and verification

None documented. With Cliqz Search shut down since 2020, a request using this name is unlikely to
come from Cliqz.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Cliqzbot` for
`Mozilla/5.0 (compatible; Cliqzbot/3.0; +http://cliqz.com/company/cliqzbot)` (a test string; no
Cliqz page confirms it today). `src/modules/identity.js` sets the identity `Cliqz` when the
unconfirmed hostname ends with `.eu-central-1.compute.amazonaws.com`: a cloud hostname, so any AWS
customer in that region passes. Cliqz documents nothing the rule could be compared to.

## Misc

On 2026-10-15, http://cliqz.com/company/cliqzbot returned a 404 page saying "The page you are
looking for no longer exists. Cliqz Search shut down in 2020." The site's imprint still names Cliqz
GmbH, Munich.

## Sources

- https://cliqz.com/company/cliqzbot (checked 2026-10-15, 404)
- https://cliqz.com/announcement.html (checked 2026-10-15)
- https://cliqz.com/imprint.html (checked 2026-10-15)
