---
name: meta-webindexer
operator: Meta
website: https://www.meta.com
documentation: https://developers.facebook.com/docs/sharing/webmasters/web-crawlers
category: ai-search
robots_txt_token: meta-webindexer
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: null
  hostnames: []
hyperwatch:
  family: meta-webindexer
  identity: Meta
last_checked: 2026-11-19
---

# meta-webindexer

## Description

meta-webindexer (Meta-WebIndexer) is a Meta crawler that "navigates the web to improve Meta AI
search result quality for users". Meta says that allowing it "helps us cite and link to your
content in Meta AI's responses".

## Behavior

Meta says its crawlers may cache `robots.txt` for up to 24 hours, so changes can take that long to
apply. Crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
meta-webindexer/1.1 (+https://developers.facebook.com/docs/sharing/webmasters/crawler)
meta-webindexer/1.1
```

The first string is from the archived December 2025 version of Meta's page. The page retrieved on
2026-10-15 shows the link as `(+/documentation/sharing/webmasters/web-crawlers)`, a relative path;
the page does not say whether the crawler now sends that form.

## Observed HTTP headers

Based on hundreds of requests seen on 2026-11-10, pages, verified as Meta by Hyperwatch 5.4.0.

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/jxl,image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (85%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/jxl,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7` (10%), `*/*` (6%) |
| `accept-language` | `en-US,en;q=0.9;q=0.9` (93%), `en-US,en;q=0.9` (4%) |
| `priority` | `u=1, i` (2%) |
| `sec-ch-ua` | `"Not-A.Brand";v="99", "Google Chrome";v="157", "Chromium";v="157"` (4%) |
| `sec-ch-ua-mobile` | `?0` (4%) |
| `sec-ch-ua-platform` | `"Windows"` (2%), `"macOS"` (2%) |
| `sec-fetch-dest` | `image` (85%), `document` (10%), `empty` (2%) |
| `sec-fetch-mode` | `no-cors` (85%), `navigate` (10%), `cors` (2%) |
| `sec-fetch-site` | `same-site` (73%), `cross-site` (10%), `none` (10%), and 1 other value |
| `sec-fetch-storage-access` | `active` (10%) |
| `sec-fetch-user` | `?1` (10%) |
| `upgrade-insecure-requests` | `1` (10%) |

## Blocking with robots.txt

```
User-agent: meta-webindexer
Disallow: /
```

Blocking it does not block Meta's other crawlers (`facebookexternalhit`, `meta-externalagent`,
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

Meta's page, checked again on 2026-11-19, says nothing about Web Bot Auth (RFC 9421). Yet
`https://www.meta.com` publishes a key directory,
https://www.meta.com/.well-known/http-message-signatures-directory: on 2026-11-19 it held five
`OKP` / `Ed25519` keys, each `kid` being the key's JWK thumbprint, so a signature's `keyid` finds a
key either way. The directory signs its own response (`tag="http-message-signatures-directory"`).

According to a comment on Hyperwatch's issue #728, and to a blog post at Tin
Computer on Meta's Muse agent, the requests signed with these keys carry `Signature-Agent: "https://www.meta.com"`
and the user agent `meta-webindexer/1.1 (+https://developers.facebook.com/docs/sharing/webmasters/crawler)`,
but do not come from Meta's network: they come from Cloudflare (AS13335), from
`2606:54c1:1::/48`, with a new address on almost every request. The same report says that the
`meta-webindexer` requests from Meta's own network are never signed, and that signatures were
missing entirely on some days (10 and 11 November 2026). Meta does not document any of this.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1, which Hyperwatch 5.7.0 depends on, returns the family
`meta-webindexer` for both strings. In `src/modules/identity.js`, Hyperwatch sets the identity
`Meta` for the families `meta-externalagent`, `meta-webindexer` and `Hyperlink` when the address is
in the published list `src/data/meta-ips.json`, the AS32934 routes from RADb written by
`node scripts/fetch-ips.js`. In Hyperwatch `main` (after 5.7.0) the file holds 59 ranges (50 IPv4,
9 IPv6), the same as the live query on 2026-10-15.

In Hyperwatch `main` (after 5.7.0, not released yet), a verified signature of
`https://www.meta.com` gives the identity `Meta Agent`, whatever the user agent ("signed only",
checked before the family rules; needs the `webbotauth` module). A signed `meta-webindexer` request
therefore gets `Meta Agent`, not `Meta`, wherever it comes from. Hyperwatch's pull request #753
explains the split by the report above: the signed requests do not come from the crawler that Meta's
addresses identify. Hyperwatch 5.7.0 does not know this signer.

## Misc

- Meta's other crawlers: `facebookexternalhit` (link previews), `meta-externalagent` (AI training
  and indexing), `meta-externalads` (advertising) and `meta-externalfetcher` (user-requested
  fetches, which may bypass `robots.txt`).
- Meta's contact for crawler questions is webmasters@meta.com.
- According to the same comment and blog post, the signed
  `meta-webindexer` requests are one step of a fetch by Muse, Meta's personal AI agent, of a link
  a user gave it. The same Cloudflare range sends three requests per link: a `HEAD` with a stock
  Chrome 138 on Linux user agent, about 10 seconds later the signed `meta-webindexer` `GET`, then,
  within 2 seconds, a request with the user agent
  `HatchFeed/1.0 (+https://agent.meta.ai; link preview)`, which also fetches the page's preview
  images. It reports that Muse never requested `robots.txt`. `https://agent.meta.ai` redirects to
  `https://muse.ai/` (checked 2026-11-19). Meta's crawler page does not list Muse or HatchFeed.
  `@hyperwatch/useragent` 4.1.1 parses that user agent as the family `HatchFeed`, for which
  Hyperwatch has no rule.

## Sources

- https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-11-19)
- https://web.archive.org/web/20251228060335/https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- whois.radb.net, query `-i origin AS32934` (checked 2026-10-15)
- https://www.meta.com/.well-known/http-message-signatures-directory (checked 2026-11-19)
- https://github.com/hyperwatch/hyperwatch/issues/728#issuecomment-6917769244 (checked 2026-11-19)
- https://tin.computer/blog/meta-muse-hatchfeed-user-agent (checked 2026-11-19)
- https://agent.meta.ai/ (checked 2026-11-19)
- https://github.com/hyperwatch/hyperwatch/pull/753 (checked 2026-11-19)
