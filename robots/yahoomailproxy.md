---
name: YahooMailProxy
operator: Yahoo
website: https://www.yahoo.com
documentation: https://senders.yahooinc.com/mail-proxy-servers/
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: ip-list
  ip_list: https://geoip.yahoo.net/georeport.csv
  hostnames: []
hyperwatch:
  family: null
  identity: Yahoo
last_checked: 2026-10-15
---

# YahooMailProxy

## Description

Yahoo Mail Proxy fetches the content of URLs embedded in emails sent to Yahoo Mail users, such as
images, and serves it to them. Yahoo says this improves its users' security and reduces network
use.

## Behavior

Yahoo says requests for images, and possibly other assets embedded in emails, come from the
addresses below, and asks senders not to rate-limit or block them so that recipients do not see
broken emails. Request rate, caching and `robots.txt` handling are not documented.

## User agents

Exact strings, one per line:

```
YahooMailProxy; https://senders.yahooinc.com/mail-proxy-servers
```

The older Yahoo help page (https://help.yahoo.com/kb/SLN28749.html) now only links to the page
above. Hyperwatch's parser recognizes an older string,
`YahooMailProxy; https://help.yahoo.com/kb/yahoo-mail-proxy-SLN28749.html`, which Yahoo no longer
documents.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

No token is documented, and Yahoo does not say whether the proxy reads `robots.txt`.

## IP ranges and verification

Yahoo lists 13 IPv4 and 5 IPv6 ranges on the page, and links to "the latest list of IPs" at
https://geoip.yahoo.net/georeport.csv. That file is a geolocation feed (prefix, country, region,
city), with no date in it: on 2026-10-15 it held 594 prefixes (485 IPv4, 109 IPv6), and the server
gave its last modification as 2025-11-15. It does not say which prefixes the proxy uses. No reverse
DNS hostname or ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns no family for the documented string, and the family
`YahooMailProxy` for the older one. `src/modules/identity.js` sets the identity `Yahoo` for the
family `YahooMailProxy` when the reverse DNS hostname ends with `.yahoo.net`.

Where it falls short:

- the documented user agent is not recognized, so it never gets an identity;
- the rule reads the unconfirmed hostname, and the `.yahoo.net` suffix is not documented by Yahoo;
- Hyperwatch does not use the ranges on the page or the linked list.

## Misc

- Hyperwatch also sets the identity `Yahoo` for the family `Yahoo` when the hostname ends with
  `.crawl.yahoo.net`.

## Sources

- https://senders.yahooinc.com/mail-proxy-servers/ (checked 2026-10-15)
- https://help.yahoo.com/kb/SLN28749.html (checked 2026-10-15)
- https://geoip.yahoo.net/georeport.csv (checked 2026-10-15)
