---
name: facebookexternalhit
operator: Meta
website: https://www.facebook.com
documentation: https://developers.facebook.com/docs/sharing/webmasters/web-crawlers
category: social-preview
robots_txt_token: facebookexternalhit
respects_robots_txt: partial
verification:
  method: ip-list
  ip_list: null
  hostnames: []
hyperwatch:
  family: FacebookBot
  identity: Facebook
last_checked: 2026-10-15
---

# facebookexternalhit

## Description

facebookexternalhit is Meta's link preview fetcher. When a link is shared on Meta apps (Facebook,
Instagram, Messenger), it fetches the page to read its title, description and image, usually from
Open Graph tags, and shows them as a preview.

## Behavior

- It fetches pages that people share. Meta says the content must be reachable "within a few
  seconds", or the preview may not be shown.
- It may send a `Range` header. Meta asks servers to either return all needed tags within the
  requested bytes or ignore the header.
- Open Graph tags must be in the first 1 MB of the page, or they are cut off.
- Servers must support gzip and deflate encodings.
- Meta's crawlers may cache `robots.txt` for up to 24 hours.
- No crawl rate is documented. JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
facebookexternalhit/1.1 (+http://www.facebook.com/externalhit_uatext.php)
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_1) AppleWebKit/601.2.4 (KHTML, like Gecko) Version/9.0.1 Safari/601.2.4 facebookexternalhit/1.1 Facebot Twitterbot/1.0
```

Meta also documents the short form `facebookexternalhit/1.1`. The second string above combines
Safari, facebookexternalhit, Facebot and Twitterbot tokens. It is not documented by Meta or X on
the pages checked, so it does not by itself show that the request comes from Meta.

## Observed HTTP headers

Based on dozens of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Facebook by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `*/*` (100%) |

Never sent: `accept-language`.

## Blocking with robots.txt

```
User-agent: facebookexternalhit
Disallow: /
```

Meta states that facebookexternalhit "might bypass robots.txt when performing security or
integrity checks", such as checking for malware. Blocking it stops link previews on Meta apps.
Each of Meta's other crawlers has its own token (see Misc).

## IP ranges and verification

Meta publishes no list file. The archived December 2025 version of its crawler page said that a
crawler whose address is in the routes announced by Meta's network, AS32934, comes from Meta, and
gave this command to list them:

```
whois -h whois.radb.net -- '-i origin AS32934' | grep ^route
```

It also warned that these addresses change often. The page text retrieved on 2026-10-15 recommends
allowlisting by IP address but no longer shows the command or any ranges. No reverse DNS hostname is
documented.


## Hyperwatch

`@hyperwatch/useragent` returns the family `FacebookBot` for both strings above. In
`src/modules/identity.js`, `FacebookBot` gets the identity `Facebook` when the reverse DNS hostname
ends with `.fbsv.net`, or when the address is in `src/data/meta-ips.json`. That file holds the
AS32934 routes from RADb (55 ranges, IPv4 and IPv6), refreshed with
`node scripts/fetch-meta-ips.js`. The `.fbsv.net` suffix is Hyperwatch's own rule, not documented by
Meta.

## Misc

- Meta's other crawlers, each with its own `robots.txt` token: `meta-externalagent` (trains AI
  models and indexes content), `meta-webindexer` (Meta AI search and citations),
  `meta-externalads` (advertising) and `meta-externalfetcher` (user-requested fetches, which may
  bypass `robots.txt`). Hyperwatch gives `meta-externalagent` and `meta-webindexer` the identity
  `Meta` when the address is in `meta-ips.json`.
- Meta's contact for crawler questions is webmasters@meta.com.

## Sources

- https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- https://web.archive.org/web/20251228060335/https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
