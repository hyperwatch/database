---
name: Googlebot
operator: Google
website: https://www.google.com
documentation: https://developers.google.com/search/docs/crawling-indexing/googlebot
category: search-engine
robots_txt_token: Googlebot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://developers.google.com/static/crawling/ipranges/common-crawlers.json
  hostnames:
    - googlebot.com
hyperwatch:
  family: Googlebot
  identity: Googlebot
last_checked: 2026-10-15
---

# Googlebot

## Description

Googlebot is Google Search's crawler. It fetches pages for Google Search and the products that rely
on it (Discover, Google Images, Google Video, Google News). It comes in two types: Googlebot
Smartphone, which simulates a mobile user and makes most requests, and Googlebot Desktop. Both
share the same `robots.txt` token.

## Behavior

- Google says Googlebot "shouldn't access your site more than once every few seconds on average"
  for most sites. Site owners can reduce the crawl rate.
- It fetches the first 2 MB of a supported file type (uncompressed) and the first 64 MB of a PDF.
  Each referenced resource (CSS, JavaScript) is fetched separately under the same limit.
- It renders JavaScript: "Google Search runs JavaScript with an evergreen version of Chromium". A
  headless Chromium renders pages after crawling, when resources allow.
- Google's crawlers use HTTP/1.1 by default and may use HTTP/2; a server can opt out of HTTP/2 by
  answering `421`. They support gzip, deflate and Brotli encodings, and heuristic HTTP caching
  (`ETag` is preferred over `Last-Modified`).
- `Crawl-delay` is not supported.
- Google generally caches `robots.txt` for up to 24 hours, longer if it cannot be refreshed. Files
  over 500 KiB are cut. A `5xx` on `robots.txt` stops crawling for 12 hours, then the last cached
  copy is used for up to 30 days. A `4xx` other than `429` is treated as no `robots.txt`.

## User agents

Exact strings, one per line:

```
Googlebot
Googlebot-Image/1.0
Mozilla/5.0 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.5993.70 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/131.0.0.0 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/153.0.8010.36 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/153.0.8010.52 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/155.0.8059.39 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/155.0.8059.79 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
Mozilla/5.0 (Linux; Android 6.0.1; Nexus 5X Build/MMB29P) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.84 Mobile Safari/537.36 (compatible; Googlebot/2.1; +http://www.google.com/bot.html)
```

Google documents the smartphone and desktop strings with a placeholder `Chrome/W.X.Y.Z` that
follows the current Chrome version, and the rare `Googlebot/2.1 (+http://www.google.com/bot.html)`.
`Googlebot-Image/1.0` is the separate Googlebot Image crawler. The bare `Googlebot` string is not
documented by Google, and old Chrome versions (99, 118) in the smartphone string are also worth
verifying: anyone can send these strings.

## Observed HTTP headers

Based on dozens of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Googlebot by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `text/html,application/xhtml+xml,application/signed-exchange;v=b3,application/xml;q=0.9,*/*;q=0.8` (68%), `image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (18%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exch` (4%), `text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8` (4%), 2 other values |
| `accept-language` | `en-US` (23%) |
| `amp-cache-transform` | `(present)` (68%) |
| `from` | `googlebot(at)googlebot.com` (97%) |
| `referer` | `(present)` (22%) |
| `upgrade-insecure-requests` | `1` (4%) |

## Blocking with robots.txt

```
User-agent: Googlebot
Disallow: /
```

Blocking Googlebot also affects Discover, Google Images, Video and News. Blocking crawling does not
by itself remove a URL from results; Google recommends `noindex` for that.

Other tokens for Google's common crawlers:

- `Googlebot-Image`, `Googlebot-Video`, `Googlebot-News` (News uses the Googlebot user agents)
- `Storebot-Google` (Google Shopping)
- `Google-InspectionTool` (Search Console and testing tools)
- `GoogleOther`, `GoogleOther-Image`, `GoogleOther-Video` (no specific product, e.g. internal
  research)
- `Google-CloudVertexBot` (crawls requested by site owners for Vertex AI Agents)
- `Google-Extended`: a control token only, with no user agent of its own. It decides whether
  content crawled by Google may be used to train Gemini models and for grounding in Gemini Apps and
  Vertex AI. It does not affect Search inclusion or ranking.

Common crawlers always respect `robots.txt` for automatic crawls. Special-case crawlers (such as
`AdsBot`) may ignore the `*` group with the publisher's agreement.

## IP ranges and verification

- IP list for common crawlers, Googlebot included:
  https://developers.google.com/static/crawling/ipranges/common-crawlers.json. JSON object with
  `creationTime` and a `prefixes` array of `{"ipv4Prefix": ...}` or `{"ipv6Prefix": ...}` objects.
  On the check date it held 317 prefixes (170 IPv4, 147 IPv6), `creationTime` 2026-10-14. The older
  URL https://developers.google.com/static/search/apis/ipranges/googlebot.json still serves the
  same file.
- Reverse DNS: `crawl-***-***-***-***.googlebot.com` or `geo-crawl-***-***-***-***.geo.googlebot.com`,
  confirmed by a forward lookup that returns the same address.
- Other Google lists: `special-crawlers.json` (hostnames under `google.com`),
  `user-triggered-fetchers.json`, `user-triggered-fetchers-google.json` and
  `user-triggered-agents.json`, all under `https://developers.google.com/static/crawling/ipranges/`,
  and all Google addresses at https://www.gstatic.com/ipranges/goog.json.
- ASN: not used by Google's verification guide.


## Hyperwatch

`@hyperwatch/useragent` returns the family `Googlebot` for the `Googlebot`, `Googlebot/2.1` and
smartphone strings, and `Googlebot-Image` for `Googlebot-Image/1.0`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `Googlebot` for the family `Googlebot` on an
unconfirmed hostname ending with `.googlebot.com` or the published list (`googlebot-ips.json`,
Google's `common-crawlers.json`). `Googlebot-Image` has no rule of its own: it gets `Googlebot` only
through the fallback for any request whose unconfirmed hostname ends with `.googlebot.com` when no
other rule matched, and the list is not checked for it. Google documents a forward lookup back to
the same address; the hostname is still not confirmed.

## Misc

- Google's crawler documentation moved from `developers.google.com/search/docs/crawling-indexing/`
  to `developers.google.com/crawling/docs/`; both locations were used here.

## Sources

- https://developers.google.com/search/docs/crawling-indexing/googlebot (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/google-common-crawlers (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/overview-google-crawlers (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/verify-google-requests (checked 2026-10-15)
- https://developers.google.com/crawling/docs/robots-txt/robots-txt-spec (checked 2026-10-15)
- https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics (checked 2026-10-15)
- https://developers.google.com/static/crawling/ipranges/common-crawlers.json (checked 2026-10-15)
- https://developers.google.com/static/search/apis/ipranges/googlebot.json (checked 2026-10-15)
