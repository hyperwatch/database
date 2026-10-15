---
name: Hyperlink
operator: Unknown
website: null
documentation: null
category: unknown
robots_txt_token: Hyperlink
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Hyperlink
  identity: Meta
last_checked: 2026-10-15
---

# Hyperlink

## Description

Hyperlink is a user agent name whose operator could not be established. Hyperwatch gives it the
identity `Meta` when the request comes from Meta's network, but Meta does not document a robot of
that name.

Searched on 2026-10-15: Meta's crawler page (it names `facebookexternalhit`, `meta-webindexer`,
`meta-externalads`, `meta-externalagent` and `meta-externalfetcher`, not `Hyperlink`), and web
searches for `Hyperlink/2.8` and for a Meta crawler named Hyperlink, which found nothing.

The only documented software with this name is `hyperlink`, an open-source Node.js tool that checks
the internal and external links of a website (https://www.npmjs.com/package/hyperlink). Nothing
links it to Meta: anyone can run it.

## Behavior

Not documented.

## User agents

Exact strings, one per line:

```
Hyperlink v5.0.4 (https://www.npmjs.com/package/hyperlink)
```

This is the string sent by the `hyperlink` link checker (version 5.0.4, the latest on npm on
2026-10-15; the version changes with the release). No string is documented for a Meta robot.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Hyperlink
Disallow: /
```

The token is the product name in the user agent. Whether the robot reads `robots.txt` is not
documented.

## IP ranges and verification

None published for this robot.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Hyperlink` for the string above and for strings starting
with `Hyperlink/<version>` (for example `Hyperlink/2.8`). `src/modules/identity.js` sets the
identity `Meta` when the address is in `src/data/meta-ips.json` (published list: the routes of
Meta's network AS32934 in RADb, refreshed with `node scripts/fetch-ips.js`; in Hyperwatch `main`
(after 5.3.3) 59 ranges, IPv4 and IPv6, the same as the live query on 2026-10-15). Meta documents
this check for its own crawlers, not for `Hyperlink`: the identity says the request came from Meta's
network, not that Meta documents the robot.

## Misc

Nothing else documented.

## Sources

- https://developers.facebook.com/docs/sharing/webmasters/web-crawlers (checked 2026-10-15)
- https://www.npmjs.com/package/hyperlink (via https://registry.npmjs.org/hyperlink/latest, checked 2026-10-15)
- https://github.com/Munter/hyperlink/blob/master/lib/index.js (checked 2026-10-15)
