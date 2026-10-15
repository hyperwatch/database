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
last_checked: 2026-10-15
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

No requests from this robot were captured with their headers yet.

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
Hyperwatch `main` (after 5.3.3) the file holds 59 ranges, the same as the live query on 2026-10-15.

## Misc

- Meta's other crawlers: `facebookexternalhit` (link previews), `meta-webindexer` (Meta AI search
  and citations), `meta-externalads` (advertising) and `meta-externalfetcher` (user-requested
  fetches, which may bypass `robots.txt`).
- Meta's contact for crawler questions is webmasters@meta.com.

## Sources

- https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- https://web.archive.org/web/20251228060335/https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- whois.radb.net, query `-i origin AS32934` (checked 2026-10-15)
