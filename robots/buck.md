---
name: Buck
operator: Hypefactors
website: https://hypefactors.com
documentation: https://app.hypefactors.com/media-monitoring/about.html
category: marketing
robots_txt_token: Buck
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Buck
  identity: null
last_checked: 2026-10-15
---

# Buck

## Description

Buck is the media monitoring crawler of Hypefactors, a PR software platform. It discovers, scans
and follows links between web pages so that brands and organisations can find coverage that
mentions them.

## Behavior

Hypefactors says Buck respects `robots.txt`, follows established crawling etiquette, and adapts to
how often a site is updated. It stores data temporarily and deletes data older than 90 days.

Crawl rate, `Crawl-delay` support, JavaScript rendering and how often it reads `robots.txt` are not
documented.

## User agents

```
Buck/2.6.0; (+https://app.hypefactors.com/media-monitoring/about.html)
```

Hypefactors does not publish the string. Third-party directories list older versions (2.5.6,
2.4.2, 2.3.2).

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Buck
Disallow: /
```

Hypefactors does not name the token; `Buck` is the product name in the user agent. The operator
also accepts removal requests by email (vyn@hypefactors.com) with the domain name.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS43515 Google Ireland Limited: `35.209.183.0/24`, `35.209.59.0/24`, `35.208.247.0/24`, `35.208.251.0/24`, `35.209.231.0/24`, `35.208.145.0/24`, `35.208.59.0/24`, `35.209.157.0/24`, and 7 more

Reverse DNS hostnames:

- `*.bc.googleusercontent.com` (forward-confirmed)

## Hyperwatch

`@hyperwatch/useragent` parses the user agent as family `Buck`. `src/modules/identity.js` has no
rule for it, so it gets no identity.

## Misc

Nothing else documented.

## Sources

- https://app.hypefactors.com/media-monitoring/about.html (checked 2026-10-15)
- https://knownagents.com/agents/buck (checked 2026-10-15)
