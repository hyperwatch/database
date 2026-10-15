---
name: Google Favicon
operator: Google
website: https://www.google.com
documentation: null
category: other
robots_txt_token: Googlebot-Image
respects_robots_txt: partial
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Google Favicon
  identity: Google
last_checked: 2026-10-15
---

# Google Favicon

## Description

Google Favicon was a Google fetcher that "retrieves favicons for various services". Google listed
it in its crawler documentation until 2023: it is in the archived copy of 2 March 2023 and absent
from the copy of 2 June 2023. Google's current list of crawlers and fetchers does not mention it.

## Behavior

The archived documentation said that "for user-initiated requests, Google Favicon ignores
robots.txt rules". Nothing else was documented.

Today, Google's favicon documentation for Search says that Googlebot-Image must be able to crawl
the favicon file and Googlebot the home page. It does not mention Google Favicon.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.75 Safari/537.36 Google Favicon
```

This is the string from the archived Google documentation (2020 to 2023).

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

The archived documentation gave two tokens, `Googlebot-Image` and `Googlebot`:

```
User-agent: Googlebot-Image
Disallow: /
```

User-initiated requests ignored `robots.txt`. Blocking these tokens also blocks Googlebot-Image or
Googlebot for Google Search.

## IP ranges and verification

None published for this fetcher: it is not in Google's current documentation, so Google does not
say which of its address lists it uses. Google's general verification page lists, for its
user-triggered fetchers, the reverse DNS names `google-proxy-***-***-***-***.google.com` (addresses
in `user-triggered-fetchers-google.json`) and `***-***-***-***.gae.googleusercontent.com`
(addresses in `user-triggered-fetchers.json`), confirmed by a forward lookup. The second suffix
belongs to Google Cloud customers' App Engine apps.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Google Favicon`. In `src/modules/identity.js`,
Hyperwatch sets the identity `Google` for the families `Google`, `GoogleDocs`, `docs.google.com`,
`Google Favicon` and `GoogleImageProxy` when the reverse DNS hostname (not forward-confirmed) ends
with `.google.com`. It uses no address list for them:
`src/data/google-user-triggered-fetchers-ips.json` (Google's `user-triggered-fetchers.json`, fetched
by `node scripts/fetch-ips.js`) is not read by `identity.js` in Hyperwatch `main` (after 5.3.3).

## Misc

- Other Google fetchers that Hyperwatch identifies as `Google`: GoogleDocs and GoogleImageProxy.

## Sources

- https://web.archive.org/web/20230302032029/https://developers.google.com/search/docs/crawling-indexing/overview-google-crawlers (checked 2026-10-15)
- https://web.archive.org/web/20230602052051/https://developers.google.com/search/docs/crawling-indexing/overview-google-crawlers (checked 2026-10-15)
- https://web.archive.org/web/20200101210337/https://support.google.com/webmasters/answer/1061943?hl=en (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/overview-google-crawlers (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/google-user-triggered-fetchers (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/verify-google-requests (checked 2026-10-15)
- https://developers.google.com/search/docs/appearance/favicon-in-search (checked 2026-10-15)
