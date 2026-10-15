---
name: Neevabot
operator: Neeva (shut down in 2023)
website: https://neeva.com
documentation: https://neeva.com/neevabot
category: search-engine
robots_txt_token: Neevabot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Neevabot
  identity: Neevabot
last_checked: 2026-10-15
---

# Neevabot

## Description

Neevabot was the crawler of Neeva, an ad-free search engine. According to Wikipedia, Neeva used its
own crawler alongside partners' results, shut down in June 2023 and was bought by Snowflake Inc.
According to CNBC (2023-05-20), Neeva announced on May 20, 2023 that it would shut down its
consumer search product.

## Behavior

Not documented: the operator's page could not be read (see below).

## User agents

The operator's page could not be read, so no documented string is available. The URL in the user
agent known to Hyperwatch is `https://neeva.com/neevabot`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Neevabot
Disallow: /
```

The token is the robot's name; whether it obeyed `robots.txt` is not documented on any page that
could be read.

## IP ranges and verification

None documented on any page that could be read. With Neeva shut down, a request using this name
is unlikely to come from Neeva.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Neevabot` for
`Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.114 Safari/537.36 (compatible; Neevabot/1.0; +https://neeva.com/neevabot)`
(a test string; Neeva's page could not be read to confirm it). `src/modules/identity.js` sets the
identity `Neevabot` when the unconfirmed hostname ends with `.neevabot.com`. On 2026-10-15 the
domain `neevabot.com` was not registered (whois: no match), and Neeva documents nothing the rule
could be compared to.

## Misc

On 2026-10-15, https://neeva.com/neevabot returned a "Redirecting..." page that runs a script, with
headers referring to `parklogic.com`, a domain parking service. Neither curl nor WebFetch could read
the original documentation, and the Internet Archive refused requests that day.

## Sources

- https://neeva.com/neevabot (checked 2026-10-15, not readable)
- https://en.wikipedia.org/wiki/Neeva (checked 2026-10-15)
- https://www.cnbc.com/2023/05/20/neeva-co-founded-by-a-former-google-exec-to-shut-down-its-consumer-search-product-and-focus-on-ai.html (2023-05-20, checked 2026-10-15)
