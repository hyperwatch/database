---
name: amazon-Quick-on-behalf-of
operator: Amazon Web Services
website: https://aws.amazon.com/quick/
documentation: https://docs.aws.amazon.com/quick/latest/userguide/web-crawler-integration.html
category: other
robots_txt_token: amazon-Quick-on-behalf-of-<UUID>
respects_robots_txt: yes
verification:
  method: ip-list
  ip_list: https://docs.aws.amazon.com/quick/latest/userguide/regions.html
  hostnames: []
hyperwatch:
  family: amazon-Quick-on-behalf-of
  identity: Amazon Quick
last_checked: 2026-10-15
---

# amazon-Quick-on-behalf-of

## Description

This is the Web Crawler integration of Amazon Quick, an AWS service. Quick customers use it to
"create knowledge bases from website content by crawling and indexing web pages". The crawl is set
up by each customer, who chooses the start URLs; the user agent carries an identifier that differs
from one setup to another. AWS says the integration "supports data ingestion only".

## Behavior

From AWS's documentation:

- The customer sets the crawl depth (0 to 10, default 1) and the maximum links followed per page
  (default 100, up to 1,000).
- The first sync is a full crawl; later syncs capture changes only. Failed requests are retried.
- It "executes JavaScript and renders page content", but does not click, scroll or hover. A
  customer-set wait time (default 1 second) applies after the page is ready.
- It looks for sitemaps by appending `sitemap.xml`, `sitemap_index.xml`, `sitemap/sitemap.xml`,
  `sitemap/sitemap_index.xml`, `sitemaps/sitemap.xml` and `sitemap/index.xml` to the start URLs. It
  does not use `Sitemap` lines in `robots.txt` and does not follow nested sitemap indexes.
- It can crawl sites behind a login (basic, form or SAML authentication), with credentials the
  customer provides.
- It only supports IPv4.

## User agents

Exact strings, one per line:

```
amazon-Quick-on-behalf-of-<UUID>
```

AWS gives only this form; `<UUID>` is a per-setup identifier.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

AWS says the crawler honors `User-agent`, `Allow`, `Disallow` and `Crawl-delay`, reads
`robots.txt` per host, and crawls as if there were no file when it can't fetch or parse it. It also
honors the `noindex` and `nofollow` robots meta tags and the same values in an HTTP header.

AWS says the user agent can be targeted in `robots.txt`, but does not say how to match all setups
at once, since each has its own UUID. A rule naming one full user agent only applies to that setup:

```
User-agent: amazon-Quick-on-behalf-of-<UUID>
Disallow: /
```

Whether a group naming only `amazon-Quick-on-behalf-of` applies to every setup is not documented.

## IP ranges and verification

AWS publishes one `/27` per region as the "IP address range for data source connectivity", in a
table at https://docs.aws.amazon.com/quick/latest/userguide/regions.html. On 2026-10-15 it listed
26 IPv4 ranges, one per supported region. The page describes them as the ranges where Quick traffic
originates "when making outbound connections to databases"; the Web Crawler page does not say it
uses them. They are not in AWS's `ip-ranges.json`. No reverse DNS hostname or ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `amazon-Quick-on-behalf-of` for a user agent ending in a
UUID. In `src/modules/identity.js`, Hyperwatch sets the identity `Amazon Quick` when the address is
in `src/data/amazon-quick-ips.json`, copied by hand from the regions table; on 2026-10-15 it held
the same 26 ranges as the table.

## Misc

- AWS documents a troubleshooting step for blocked crawls: verify the site "is reachable from the
  AWS Region where the Amazon Quick instance is set up".
- This crawler is unrelated to Amazonbot, Amzn-SearchBot and Amzn-User.

## Sources

- https://docs.aws.amazon.com/quick/latest/userguide/web-crawler-integration.html (checked 2026-10-15, as `.md`)
- https://docs.aws.amazon.com/quick/latest/userguide/regions.html (checked 2026-10-15)
