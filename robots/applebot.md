---
name: Applebot
operator: Apple
website: https://www.apple.com
documentation: https://support.apple.com/en-us/119829
category: search-engine
robots_txt_token: Applebot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://search.developer.apple.com/applebot.json
  hostnames:
    - applebot.apple.com
hyperwatch:
  family: Applebot
  identity: Applebot
last_checked: 2026-10-15
---

# Applebot

## Description

Applebot is Apple's web crawler. Its data powers search features in Spotlight, Siri and Safari.
Apple says crawled data may also be used to train its foundation models for generative AI
features, and to provide context for AI-generated answers in Siri and Search that link to sources.

## Behavior

Apple documents:

- Applebot follows standard `robots.txt` directives aimed at it.
- It does not follow `Crawl-delay`.
- Its crawl rate adjusts automatically when a site slows down or returns errors, and Apple caches
  crawled content to avoid unnecessary requests.
- It may render pages in a browser. If JavaScript, CSS or XHR resources are blocked by
  `robots.txt`, rendering may fail.
- It supports `noindex`, `nosnippet`, `nofollow`, `none` and `all` in robots meta tags and in the
  `X-Robots-Tag` header, including Applebot-specific forms such as
  `<meta name="applebot" content="nosnippet">`. `nosnippet` also excludes content from AI answer
  context.

How often it reads `robots.txt` is not documented.

## User agents

```
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.0 Safari/605.1.15 (Applebot/0.1; +http://www.apple.com/go/applebot)
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.4 Safari/605.1.15 (Applebot/0.1; +http://www.apple.com/go/applebot)
```

Apple documents this mobile string too:

```
Mozilla/5.0 (iPhone; CPU iPhone OS 17_4_1 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.4.1 Mobile/15E148 Safari/604.1 (Applebot/0.1; +http://www.apple.com/go/applebot)
```

Apple says it occasionally updates the browser version while keeping the format.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Applebot by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (89%), `*/*` (11%) |
| `accept-language` | `en-US,en;q=0.90` (11%) |
| `referer` | `(present)` (<1%) |
| `sec-fetch-dest` | `empty` (11%), `document` (<1%) |
| `sec-fetch-mode` | `cors` (11%), `navigate` (<1%) |
| `sec-fetch-site` | `same-origin` (11%), `cross-site` (<1%) |

## Blocking with robots.txt

```
User-agent: Applebot
Disallow: /
```

If `robots.txt` does not mention Applebot but mentions Googlebot, Applebot follows the Googlebot
rules.

`Applebot-Extended` is a separate token that does not crawl. It controls whether content already
crawled by Applebot may be used to train Apple's foundation models. Disallowing it does not remove
pages from Apple's search results, and it is not used for ranking:

```
User-agent: Applebot-Extended
Disallow: /
```

Traffic with `User-Agent: iTMS` does not follow `robots.txt`; it only fetches URLs tied to
registered Apple Podcasts content.

## IP ranges and verification

Apple documents two methods:

- Reverse DNS: Applebot addresses resolve to hostnames under `*.applebot.apple.com` (for example
  `17-58-101-179.applebot.apple.com`). Confirm with a forward lookup back to the same address.
- IP list: https://search.developer.apple.com/applebot.json, in the Googlebot JSON format
  (`creationTime` and a `prefixes` array of `ipv4Prefix` objects). When checked it held 24 IPv4
  ranges (`/27` and `/28`), no IPv6, `creationTime` 2026-09-15.

No ASN is documented by Apple.


## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `Applebot`. In `src/modules/identity.js`,
Hyperwatch sets identity `Applebot` when the reverse DNS hostname ends with `.apple.com`. This
check uses the plain reverse DNS hostname, not the forward-confirmed one, and does not use the
published IP list.

## Misc

Apple says Applebot also powers other user agents, including Podcasts. Contact:
applebot@apple.com.

## Sources

- https://support.apple.com/en-us/119829 (checked 2026-10-15)
- https://search.developer.apple.com/applebot.json (checked 2026-10-15)
