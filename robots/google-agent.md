---
name: Google-Agent
operator: Google
website: https://www.google.com
documentation: https://developers.google.com/crawling/docs/crawlers-fetchers/google-agent
category: ai-assistant
robots_txt_token: null
respects_robots_txt: no
verification:
  method: ip-list
  ip_list: https://developers.google.com/static/crawling/ipranges/user-triggered-agents.json
  hostnames: []
hyperwatch:
  family: Google-Agent
  identity: Google Agent
last_checked: 2026-11-12
---

# Google-Agent

## Description

Google-Agent is one of Google's user-triggered fetchers. Google says it is used by agents hosted on
Google infrastructure to navigate the web and perform actions upon user request. Google does not
name the products that use it.

## Behavior

Google says user-triggered fetchers "generally ignore robots.txt rules" because a user requested
the fetch. Which actions the agents perform beyond navigating (forms, logins) is not documented.
Crawl rate and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/W.X.Y.Z Mobile Safari/537.36 (compatible; Google-Agent; +https://developers.google.com/crawling/docs/crawlers-fetchers/google-agent)
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko; compatible; Google-Agent; +https://developers.google.com/crawling/docs/crawlers-fetchers/google-agent) Chrome/W.X.Y.Z Safari/537.36
```

Google writes `W.X.Y.Z` for the Chrome version, which changes.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Google names no `robots.txt` token for Google-Agent, and says user-triggered
fetchers generally ignore `robots.txt` rules.

## IP ranges and verification

Google says Google-Agent uses the ranges of
https://developers.google.com/static/crawling/ipranges/user-triggered-agents.json, in the Googlebot
format (`creationTime` and a `prefixes` array of `ipv4Prefix` / `ipv6Prefix` objects). On
2026-11-10 it held 20 prefixes, with `creationTime` 2026-11-09. They are not in any of Google's
three other lists.

Google gives two reverse DNS masks for user-triggered fetchers,
`***-***-***-***.gae.googleusercontent.com` and `google-proxy-***-***-***-***.google.com`, without
saying which one Google-Agent uses.

Google also says it is experimenting with Web Bot Auth for Google-Agent, with the identity
`https://agent.bot.goog`: a subset of requests are signed, with the `Signature-Agent` header set to
`g="https://agent.bot.goog"` (a dictionary member labelled `g`, the label of the `Signature` and
`Signature-Input` to check), and Google says to fall back to the address check as not all requests
are signed. On 2026-11-12 the key directory
(https://agent.bot.goog/.well-known/http-message-signatures-directory) held 5 `OKP` / `Ed25519`
keys, each with a short `kid` (such as `mhxuPw`) that is not its JWK thumbprint. The directory's
own signature uses a `kid` as its `keyid`, and Hyperwatch's code says Google signs its requests the
same way; Google's pages don't say.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Google-Agent` for both strings. In Hyperwatch 5.6.0,
`src/modules/identity.js` first sets the identity `Google Agent` on a verified signature of
`https://agent.bot.goog`, whatever the user agent ("signed only"; needs the `webbotauth` module,
off by default, which finds Google's keys by their `kid`). There is no rule for the family: when no
other rule set an identity, Google's pools are checked for any user agent, in this order. An
address in Google's special-case crawlers' list or a forward-confirmed
`rate-limited-proxy-*.google.com` name gives `Google Special Crawlers`. An address in the published
list `google-user-triggered-agents-ips.json`, fetched from `user-triggered-agents.json`, gives
`Google Agent`. An address in Google's own user-triggered fetchers' list or a forward-confirmed
`google-proxy-*.google.com` name gives `Google Proxy`. Unsigned, the list is the only check for
`Google Agent`: Google gives no reverse DNS name for Google-Agent, and an unsigned `Google-Agent`
user agent from the Google Proxy pool gets `Google Proxy`.

## Misc

Google's other user-triggered fetchers include [GoogleDocs](googledocs.md) and
[GoogleImageProxy](googleimageproxy.md); its special-case crawlers include
[AdsBot-Google](adsbot-google.md).

## Sources

- https://developers.google.com/crawling/docs/crawlers-fetchers/google-agent (checked 2026-11-10)
- https://developers.google.com/crawling/docs/crawlers-fetchers/google-user-triggered-fetchers (checked 2026-11-10)
- https://developers.google.com/static/crawling/ipranges/user-triggered-agents.json (checked 2026-11-10)
- https://developers.google.com/crawling/docs/crawlers-fetchers/web-bot-auth (checked 2026-11-12)
- https://agent.bot.goog/.well-known/http-message-signatures-directory (checked 2026-11-12)
