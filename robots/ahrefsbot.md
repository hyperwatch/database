---
name: AhrefsBot
operator: Ahrefs
website: https://ahrefs.com
documentation: https://ahrefs.com/robot
category: seo
robots_txt_token: AhrefsBot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://api.ahrefs.com/v3/public/crawler-ip-ranges
  hostnames: [".ahrefs.com", ".ahrefs.net"]
hyperwatch:
  family: AhrefsBot
  identity: Ahrefs
last_checked: 2026-10-15
---

# AhrefsBot

## Description

AhrefsBot is the main web crawler of Ahrefs. Ahrefs says it builds the database behind its
marketing platform and behind Yep, the search engine Ahrefs develops.

## Behavior

Ahrefs says AhrefsBot obeys `Disallow` and `Allow` rules and `Crawl-delay`. `Crawl-delay` is
followed for HTML pages, but not when the robot renders JavaScript: it may then fetch several
assets (images, scripts, stylesheets) at once. It caches frequently requested files during a
crawl.

It slows down by itself when a site returns 4xx or 5xx status codes. Ahrefs suggests returning
such codes to reduce its rate during an outage.

Changes to `robots.txt` are picked up "before the next scheduled crawl". If `robots.txt` contains
errors, the robot keeps crawling as before. Crawl frequency is not documented otherwise.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; AhrefsBot/7.0; +http://ahrefs.com/robot/)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: AhrefsBot
Disallow: /
```

To slow it down instead:

```
User-agent: AhrefsBot
Crawl-Delay: 10
```

The value is in seconds. The site audit crawler has its own token, `AhrefsSiteAudit` (see
[AhrefsSiteAudit](ahrefssiteaudit.md)).

## IP ranges and verification

Ahrefs says it crawls from published IP ranges, and that the reverse DNS name of its addresses
always ends with `ahrefs.com` or `ahrefs.net`. It does not say whether that name resolves back to
the address.

Two lists cover both AhrefsBot and AhrefsSiteAudit:

- https://api.ahrefs.com/v3/public/crawler-ip-ranges: JSON with a `prefixes` array of objects
  with an `ipv4Prefix` key. On 2026-10-15 it held 81 IPv4 prefixes and no IPv6 prefix.
- https://api.ahrefs.com/v3/public/crawler-ips: the same addresses one by one, JSON with an `ips`
  array of objects with an `ip_address` key. On 2026-10-15 it held 10,350 IPv4 addresses.

Neither file says when it was generated. The help article that lists the same ranges as text was
dated 2026-09-03. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` parses the string above as family `AhrefsBot`. In Hyperwatch `main` (after
5.3.3), `src/modules/identity.js` sets the identity `Ahrefs` for the families `AhrefsBot` and
`AhrefsSiteAudit` on an unconfirmed hostname ending with `.ahrefs.com` or the published list
(`ahrefs-ips.json`, fetched from `crawler-ip-ranges`). The hostname is not confirmed with a forward
lookup, and `.ahrefs.net`, which Ahrefs documents, is not accepted: such an address passes only
through the list.

## Misc

Ahrefs says both of its crawlers are listed as verified bots by Cloudflare. Questions about
crawling go to the support address given on the robot page.

## Sources

- https://ahrefs.com/robot (checked 2026-10-15)
- https://api.ahrefs.com/v3/public/crawler-ip-ranges (checked 2026-10-15)
- https://api.ahrefs.com/v3/public/crawler-ips (checked 2026-10-15)
- https://help.ahrefs.com/en/articles/78658-what-is-the-list-of-your-ip-ranges (checked 2026-10-15)
