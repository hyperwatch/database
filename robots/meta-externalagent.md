---
name: meta-externalagent
operator: Meta
website: https://www.meta.com
documentation: https://developers.facebook.com/docs/sharing/webmasters/web-crawlers
category: ai-training
robots_txt_token: meta-externalagent
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: null
  hostnames: []
hyperwatch:
  family: meta-externalagent
  identity: Meta
last_checked: 2026-11-10
---

# meta-externalagent

## Description

meta-externalagent (Meta-ExternalAgent) is a Meta crawler that "crawls the web for use cases such
as training foundation AI models or improving products by indexing content directly".

## Behavior

Meta says its crawlers may cache `robots.txt` for up to 24 hours, so changes can take that long to
apply. Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
meta-externalagent/1.1 (+https://developers.facebook.com/docs/sharing/webmasters/crawler)
meta-externalagent/1.1
```

The first string is from the archived December 2025 version of Meta's page. The page retrieved on
2026-10-15 shows the link as `(+/documentation/sharing/webmasters/web-crawlers)`, a relative path;
the page does not say whether the crawler now sends that form.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-11-10, pages, verified as Meta by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/jxl,image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (98%), `*/*` (2%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/jxl,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` (<1%) |
| `accept-language` | `en-US,en;q=0.9;q=0.9` (94%), `en-US,en;q=0.9` (4%) |
| `priority` | `u=1, i` (1%) |
| `sec-ch-ua` | `"Not-A.Brand";v="99", "Google Chrome";v="157", "Chromium";v="157"` (4%) |
| `sec-ch-ua-mobile` | `?0` (4%) |
| `sec-ch-ua-platform` | `"Windows"` (4%) |
| `sec-fetch-dest` | `image` (98%), `empty` (1%), `iframe` (<1%) |
| `sec-fetch-mode` | `no-cors` (98%), `cors` (1%), `navigate` (<1%) |
| `sec-fetch-site` | `cross-site` (95%), `same-site` (3%), `same-origin` (1%) |
| `sec-fetch-storage-access` | `active` (98%) |
| `upgrade-insecure-requests` | `1` (<1%) |

## Blocking with robots.txt

```
User-agent: meta-externalagent
Disallow: /
```

Meta's example allows everything but a directory:

```
User-agent: meta-externalagent
Allow: /
Disallow: /private/
```

Blocking it does not block Meta's other crawlers (`facebookexternalhit`, `meta-webindexer`,
`meta-externalads`, `meta-externalfetcher`), which have their own tokens.

## IP ranges and verification

Meta publishes no list file. The page retrieved on 2026-10-15 says to allowlist "either the user
agent strings or the IP addresses", the latter being more secure, but gives no addresses. The
archived December 2025 version said that a crawler whose address is in the routes announced by
AS32934, Meta's network, comes from Meta, and listed them with:

```
whois -h whois.radb.net -- '-i origin AS32934' | grep ^route
```

It warned that these addresses change often. On 2026-10-15 that query returned 1,091 routes, 59
once nested ones were removed (50 IPv4, 9 IPv6). No reverse DNS hostname is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `meta-externalagent` for both strings. In
`src/modules/identity.js`, Hyperwatch sets the identity `Meta` for the families
`meta-externalagent`, `meta-webindexer` and `Hyperlink` when the address is in
`src/data/meta-ips.json`, the AS32934 routes from RADb written by `node scripts/fetch-ips.js`. In
Hyperwatch `main` (after 5.4.0) the file holds 59 ranges, the same as the live query on 2026-10-15.

## Misc

- Meta's other crawlers: `facebookexternalhit` (link previews), `meta-webindexer` (Meta AI search
  and citations), `meta-externalads` (advertising) and `meta-externalfetcher` (user-requested
  fetches, which may bypass `robots.txt`).
- Meta's contact for crawler questions is webmasters@meta.com.

## Sources

- https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- https://web.archive.org/web/20251228060335/https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- whois.radb.net, query `-i origin AS32934` (checked 2026-10-15)
