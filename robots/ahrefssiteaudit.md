---
name: AhrefsSiteAudit
operator: Ahrefs
website: https://ahrefs.com
documentation: https://ahrefs.com/robot
category: seo
robots_txt_token: AhrefsSiteAudit
respects_robots_txt: partial
verification:
  method: both
  ip_list: https://api.ahrefs.com/v3/public/crawler-ip-ranges
  hostnames: [".ahrefs.com", ".ahrefs.net"]
hyperwatch:
  family: AhrefsSiteAudit
  identity: null
last_checked: 2026-10-15
---

# AhrefsSiteAudit

## Description

AhrefsSiteAudit is the crawler behind Site Audit, the Ahrefs tool that checks websites for
technical and on-page SEO issues. Ahrefs users point it at sites they want audited.

## Behavior

Ahrefs says the crawler renders pages. By default it obeys `robots.txt` and `Crawl-delay`, and
fetches at most 30 URLs per minute. `Crawl-delay` is not followed for the assets a rendered page
loads. Owners who verify their site in Site Audit can make it ignore `robots.txt` and
`Crawl-delay` and crawl faster on that site.

It slows down by itself when a site returns 4xx or 5xx status codes. How often it reads
`robots.txt` is not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; AhrefsSiteAudit/6.1; +http://ahrefs.com/robot/site-audit)
Mozilla/5.0 (Linux; Android 13) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/151.0.7922.173 Mobile Safari/537.36 (compatible; AhrefsSiteAudit/6.1; +http://ahrefs.com/robot/site-audit)
```

The first is the desktop user agent, the second the mobile one.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: AhrefsSiteAudit
Disallow: /
```

This does not apply to a site whose verified owner has told Site Audit to ignore `robots.txt`.
The link crawler has its own token, `AhrefsBot` (see [AhrefsBot](ahrefsbot.md)).

## IP ranges and verification

The same as AhrefsBot: Ahrefs publishes one set of lists for both crawlers, and says the reverse
DNS name of its addresses always ends with `ahrefs.com` or `ahrefs.net`. It does not say whether
that name resolves back to the address.

- https://api.ahrefs.com/v3/public/crawler-ip-ranges: JSON with a `prefixes` array of objects
  with an `ipv4Prefix` key. On 2026-10-15 it held 81 IPv4 prefixes and no IPv6 prefix.
- https://api.ahrefs.com/v3/public/crawler-ips: the same addresses one by one. On 2026-10-15 it
  held 10,350 IPv4 addresses.

Neither file says when it was generated. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses both strings above as family `AhrefsSiteAudit`.
`src/modules/identity.js` has no rule for this family, and none of the hostname or signature
fallbacks matches Ahrefs, so the identity is always null. Ahrefs documents both an IP list and a
reverse DNS suffix that could verify it.

## Misc

Documented on the same page as AhrefsBot.

## Sources

- https://ahrefs.com/robot (checked 2026-10-15)
- https://api.ahrefs.com/v3/public/crawler-ip-ranges (checked 2026-10-15)
- https://api.ahrefs.com/v3/public/crawler-ips (checked 2026-10-15)
