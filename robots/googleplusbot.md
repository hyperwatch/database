---
name: GooglePlusBot
operator: Google
website: https://www.google.com
documentation: null
category: social-preview
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: GooglePlusBot
  identity: Google Proxy
last_checked: 2026-11-10
---

# GooglePlusBot

## Description

GooglePlusBot is the name `@hyperwatch/useragent` gives to a Google fetcher whose user agent ends
with `Google (+https://developers.google.com/+/web/snippet/)`, a link to the documentation of
Google+ snippets, the previews of shared links. Google does not document this user agent in its
current lists of crawlers and fetchers: what it fetches for today is not documented.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/56.0.2924.87 Safari/537.36 Google-PageRenderer Google (+https://developers.google.com/+/web/snippet/)
```

This string was seen in requests, not taken from Google's documentation. `Google-PageRenderer`
does not appear in Google's current lists either.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Google names no `robots.txt` token for this fetcher. Google says its
user-triggered fetchers "generally ignore robots.txt rules" because a user requested the fetch.

## IP ranges and verification

None published for this user agent. Google publishes the addresses of its own user-triggered
fetchers at
https://developers.google.com/static/crawling/ipranges/user-triggered-fetchers-google.json, with
the reverse DNS mask `google-proxy-***-***-***-***.google.com`, but does not say this user agent
is one of them.

## Hyperwatch

`@hyperwatch/useragent` returns the family `GooglePlusBot`. In Hyperwatch `main` (after 5.4.0),
`src/modules/identity.js` has no rule for this family: when no other rule set an identity, it sets
`Google Proxy` for any request whose address is in the published list
(`google-user-triggered-fetchers-google-ips.json`, fetched from Google's
user-triggered-fetchers-google.json) or whose forward-confirmed hostname matches
`google-proxy-*.google.com`, `Google Special Crawlers` for Google's special-case crawlers' addresses
(checked first), and `Google Agent` for Google-Agent's addresses (checked next), whatever the user
agent. Since Google doesn't document this user agent, the identity says the request came from
Google's fetchers, not which product made it.

## Misc

Google's documented user-triggered fetchers include [GoogleDocs](googledocs.md) and
[GoogleImageProxy](googleimageproxy.md).

## Sources

- https://developers.google.com/crawling/docs/crawlers-fetchers/google-user-triggered-fetchers (checked 2026-11-10)
- https://developers.google.com/crawling/docs/crawlers-fetchers/overview-google-crawlers (checked 2026-11-10)
