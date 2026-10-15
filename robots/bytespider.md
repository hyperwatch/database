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

<!-- observed headers: to be filled -->

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

## Hyperwatch

`@hyperwatch/useragent` returns the family `Bytespider`. `src/modules/identity.js` sets the identity
`Bytespider` when the reverse-confirmed hostname ends with `.crawl.bytedance.com` or
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
