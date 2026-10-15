---
name: Twitterbot
operator: X Corp. (formerly Twitter)
website: https://x.com
documentation: https://developer.x.com/en/docs/x-for-websites/cards/guides/getting-started
category: social-preview
robots_txt_token: Twitterbot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://developer.x.com/en/docs/x-for-websites/cards/guides/troubleshooting-cards
  hostnames:
    - twttr.com
hyperwatch:
  family: Twitterbot
  identity: Twitter
last_checked: 2026-10-15
---

# Twitterbot

## Description

Twitterbot is the fetcher X (formerly Twitter) uses for URLs shared on the platform. It reads Card
metadata (`twitter:*` tags) and images to build link previews.

## Behavior

- It fetches URLs shared on X and the images they reference.
- X says its crawler "respects Google's robots.txt specification". The `robots.txt` file must be
  plain text with ASCII encoding.
- Card content is cached for 7 days after a link to the page is posted. Images are cached by URL.
- Crawl rate, `Crawl-delay` support, JavaScript rendering and how often `robots.txt` is re-read are
  not documented. Google's specification, which X follows, does not support `Crawl-delay`.

## User agents

Exact strings, one per line:

```
Twitterbot/1.0
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_1) AppleWebKit/601.2.4 (KHTML, like Gecko) Version/9.0.1 Safari/601.2.4 facebookexternalhit/1.1 Facebot Twitterbot/1.0
WoltLabSuite/5.5 (URL Unfurling; like Twitterbot)
```

X documents only the token `Twitterbot` "with version, such as Twitterbot/1.0". The second string
combines Safari, facebookexternalhit, Facebot and Twitterbot tokens and is not documented by X or
Meta. The third is sent by WoltLab Suite, forum software that unfurls links itself and says it
behaves "like Twitterbot": it does not come from X.

## Observed HTTP headers

Based on fewer than 10 requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Twitter by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (89%) |
| `finagle-ctx-com.twitter.finagle.retries` | `(present)` (100%) |
| `x-b3-flags` | `(present)` (100%) |
| `x-b3-parentspanid` | `(present)` (100%) |
| `x-b3-sampled` | `(present)` (100%) |
| `x-b3-spanid` | `(present)` (100%) |
| `x-b3-traceid` | `(present)` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: Twitterbot
Disallow: /
```

If a page with card markup is blocked, no card is shown. If an image URL is blocked, no thumbnail is
shown. X's example to allow only its fetcher:

```
User-agent: Twitterbot
Disallow:

User-agent: *
Disallow: /
```

## IP ranges and verification

X's Cards troubleshooting guide gives two methods:

- IP ranges and ASN: "Twitter's aggregate outbound IP ranges are 199.16.156.0/22, 199.59.148.0/22
  and 192.133.76.0/22. Twitter's ASNUM is AS13414." The list is published as text on that page
  (3 IPv4 ranges, no IPv6, no machine-readable file).
- Reverse DNS: the reverse lookup returns a name such as `r-199-59-150-180.twttr.com`, and a forward
  lookup of that name must return the same address.

The guide's current URL redirects to the X developer platform overview; the text above was read
from the archived copy of December 2025.


## Hyperwatch

`@hyperwatch/useragent` returns the family `Twitterbot` for `Twitterbot/1.0`. In
`src/modules/identity.js`, `Twitterbot` gets the identity `Twitter` when the reverse DNS hostname
ends with `.twttr.com` or when the address is in `199.16.156.0/22`. The other two published ranges
(`199.59.148.0/22`, `192.133.76.0/22`) are not checked. The combined Safari string parses as
`FacebookBot` (handled by the Meta rule), and the WoltLab string as `WoltLabSuite` (no identity).

## Misc

- X's Cards documentation is no longer at its old developer.x.com address; the current developer
  site has no Cards pages on the check date.

## Sources

- https://developer.x.com/en/docs/x-for-websites/cards/guides/getting-started (checked 2026-10-15, redirects to https://docs.x.com/overview)
- https://web.archive.org/web/20260101000233/https://developer.x.com/en/docs/x-for-websites/cards/guides/getting-started (checked 2026-10-15)
- https://developer.x.com/en/docs/x-for-websites/cards/guides/troubleshooting-cards (checked 2026-10-15, redirects to https://docs.x.com/overview)
- https://web.archive.org/web/20251231142717/https://developer.x.com/en/docs/x-for-websites/cards/guides/troubleshooting-cards (checked 2026-10-15)
- https://docs.x.com/sitemap.xml (checked 2026-10-15)
