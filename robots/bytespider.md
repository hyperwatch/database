---
name: Bytespider
operator: ByteDance
website: https://www.bytedance.com
documentation: null
category: unknown
robots_txt_token: Bytespider
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Bytespider
  identity: Bytespider
last_checked: 2026-10-15
---

# Bytespider

## Description

Bytespider is a crawler run by ByteDance, the company behind TikTok, Toutiao and Doubao. ByteDance
has not published a public page describing what Bytespider collects or what the data is used for.
Some of its user agents point to the Toutiao Search webmaster platform (`zhanzhang.toutiao.com`),
others to a ByteDance Lark document that requires a login, and others give the address
`spider-feedback@bytedance.com`. Third-party sources commonly describe it as collecting data for
ByteDance's AI models; this is not confirmed by ByteDance.

## Behavior

Not documented by the operator: crawl rate, `Crawl-delay` support, JavaScript rendering and
`robots.txt` caching are all unknown. Several third-party reports say Bytespider does not always
follow `robots.txt`; ByteDance has not published a statement that could be checked.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; Bytespider; spider-feedback@bytedance.com) AppleWebKit/537.36
Mozilla/5.0 (compatible; Bytespider; spider-feedback@bytedance.com) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.0.0 Safari/537.36
Mozilla/5.0 (iPhone; CPU iPhone OS 7_1_2 like Mac OS X) AppleWebKit/537.36 (KHTML, like Gecko) Version/7.0 Mobile Safari/537.36 (compatible; Bytespider; https://bytedance.sg.larkoffice.com/docx/K5bxdypulop3IIxrJb0lOjLVgFe)
Mozilla/5.0 (Linux; Android 5.0) AppleWebKit/537.36 (KHTML, like Gecko) Mobile Safari/537.36 (compatible; Bytespider; https://zhanzhang.toutiao.com/)
Mozilla/5.0 (Linux; Android 5.0) AppleWebKit/537.36 (KHTML, like Gecko) Mobile Safari/537.36 (compatible; Bytespider; spider-feedback@bytedance.com)
```

## Observed HTTP headers

Based on hundreds of requests seen on 2026-10-15, all paths (`robots.txt` and pages), verified as Bytespider by Hyperwatch.

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/heif,image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (66%), `text/html,application/xhtml+xml,application/xml;q=0.9,image/heif,image/avif,image/webp,image/apng,*/*;q=0.8,application/` (33%), `*/*` (<1%) |
| `accept-language` | `en-US,en;q=0.5` (99%), `zh,zh-CN;q=0.9` (<1%) |
| `priority` | `i` (42%), `u=0, i` (33%), `u=1, i` (25%) |
| `referer` | `(present)` (65%) |
| `sec-fetch-dest` | `image` (66%), `document` (34%) |
| `sec-fetch-mode` | `no-cors` (66%), `navigate` (33%) |
| `sec-fetch-site` | `same-site` (52%), `none` (33%), `cross-site` (15%) |
| `sec-fetch-storage-access` | `active` (15%) |
| `sec-fetch-user` | `?1` (33%) |
| `upgrade-insecure-requests` | `1` (33%) |

## Blocking with robots.txt

```
User-agent: Bytespider
Disallow: /
```

The token is the name in the user agent. ByteDance does not document which tokens it obeys or
whether it supports `Crawl-delay`.

## IP ranges and verification

None published. ByteDance does not document an IP list, reverse DNS names or an ASN for
Bytespider.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS16509 Amazon.com, Inc.: `47.128.54.0/24`, `47.128.53.0/24`, `47.128.57.0/24`, `47.128.58.0/24`, `47.128.63.0/24`, `47.128.61.0/24`, `47.128.31.0/24`, `47.128.126.0/24`, and 62 more
- AS23724 IDC, China Telecommunications Corporation: `122.14.224.0/24`, `122.14.227.0/24`
- AS4134 CHINANET BACKBONE (not a hosting network: prefixes not listed)
- AS4837 CHINA UNICOM China169 Backbone (not a hosting network: prefixes not listed)
- AS396982 Google LLC: `136.108.186.0/24`, `34.77.232.0/24`, `136.115.216.0/24`, `35.198.56.0/24`, `34.21.194.0/24`, `35.200.61.0/24`, `104.155.223.0/24`, `34.152.54.0/24`, and 44 more
- AS199524 G-Core Labs S.A.: `2a03:90c0:321::/48`, `2a03:90c0:41::/48`, `2a03:90c0:11::/48`, `93.123.17.0/24`, `92.223.124.0/24`
- AS55960 Beijing Guanghuan Xinwang Digital (not a hosting network: prefixes not listed)
- AS399244 AME Hosting LLC: `76.164.199.0/24`
- AS20012 Interworks Networking Services (not a hosting network: prefixes not listed)
- AS132892 Cloudflare, Inc.: `2a06:98c0:3600::/48`

Reverse DNS hostnames:

- `*.ap-southeast-1.compute.amazonaws.com` (forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` returns the family `Bytespider`. `src/modules/identity.js` sets the identity
`Bytespider` when the reverse DNS hostname (not confirmed by a forward lookup) ends with `.crawl.bytedance.com` or
`.ap-southeast-1.compute.amazonaws.com`. These suffixes are not documented by ByteDance. The second
one matches any AWS EC2 instance in the Singapore region, so it does not prove that a request comes
from ByteDance.

## Misc

- ByteDance also runs `TikTokSpider`. Hyperwatch checks it with the same hostname suffixes and
  gives it the identity `TikTok`.
- The Lark document linked from one user agent redirects to a login page and could not be read.

## Sources

- https://bytedance.sg.larkoffice.com/docx/K5bxdypulop3IIxrJb0lOjLVgFe (checked 2026-10-15, requires login)
- https://zhanzhang.toutiao.com/ (checked 2026-10-15)
