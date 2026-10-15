---
name: Shields.io
operator: Shields.io (open-source project)
website: https://shields.io
documentation: https://github.com/badges/shields/blob/master/doc/production-hosting.md
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Shields.io
  identity: Shields.io
last_checked: 2026-10-15
---

# Shields.io

## Description

Shields.io serves status badges (SVG images) for READMEs and web pages. To draw some badges, its
servers fetch data from third-party APIs or from a URL given in the badge address.

## Behavior

Badges that fetch a URL chosen by the badge's author include the endpoint badge
(`/endpoint?url=…`), the dynamic JSON, XML and YAML badges, and the website badge
(`/website?url=…`), which sends a `HEAD` request to report whether the site is up. These come from
the source code (`services/endpoint`, `services/dynamic`, `services/website`), not from a page about
the robot.

The production configuration sets an 8-second request timeout. The default response size limit is
10 MB (`fetchLimitBytes` in `config/default.yml`). `robots.txt` handling is not documented.

## User agents

The source builds the user agent as `<userAgentBase>/<version>`. In production, `userAgentBase` is
`Shields.io` (`config/shields-io-production.yml`), and the version is the Docker image version or
the first 7 characters of the deployed commit. A self-hosted instance sends
`shields (self-hosted)/<version>` unless configured otherwise.

```
Shields.io/<version>
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

No token is documented. Whether Shields.io reads `robots.txt` is not documented.

## IP ranges and verification

None published. The production hosting document says the badge server runs on Fly.io, behind
Cloudflare. No ranges, hostnames or ASN are documented for its outgoing requests.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Shields.io` for `Shields.io/<version>`, and `shields`
for the self-hosted default. `src/modules/identity.js` sets the identity `Shields.io` when the
reverse DNS hostname ends with `.compute-1.amazonaws.com`. This is a cloud hostname: any customer
of AWS EC2 in us-east-1 passes it. Shields.io documents its hosting on Fly.io, not AWS.

## Misc

Nothing else documented.

## Sources

- https://github.com/badges/shields/blob/master/doc/production-hosting.md (checked 2026-10-15)
- https://github.com/badges/shields/blob/master/core/base-service/got-config.js (checked 2026-10-15)
- https://github.com/badges/shields/blob/master/config/shields-io-production.yml (checked 2026-10-15)
- https://github.com/badges/shields/blob/master/config/default.yml (checked 2026-10-15)
- https://github.com/badges/shields/blob/master/services/website/website.service.js (checked 2026-10-15)
