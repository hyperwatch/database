---
name: ClatterLabsSearchBot
operator: Unknown
website: https://www.clatterai.com
documentation: null
category: unknown
robots_txt_token: ClatterLabsSearchBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: ClatterLabsSearchBot
  identity: null
last_checked: 2026-10-15
---

# ClatterLabsSearchBot

## Description

ClatterLabsSearchBot points to `https://www.clatterai.com` in its user agent. No page describes the
robot, and its operator ("Clatter Labs", by the name) could not be confirmed. Its purpose is not
documented beyond the word "Search" in its name.

## Behavior

Not documented. The user agent contains `SupabaseEdgeRuntime/1.77.0`, the name of the runtime behind
Supabase Edge Functions, which suggests the requests are sent from Supabase's hosted functions
rather than from a dedicated crawler.

## User agents

Exact strings, one per line:

```
ClatterLabsSearchBot/1.0 (+https://www.clatterai.com) (variant; SupabaseEdgeRuntime/1.77.0; ref=fauvpkcqapbflqakfthe)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: ClatterLabsSearchBot
Disallow: /
```

The token is the product name in the user agent. Whether the robot reads `robots.txt` is not
documented.

## IP ranges and verification

None published.

### Observed

Requests with this user agent seen between 2026-10-12 and 2026-10-15, compared with what the operator publishes. Only differences are listed.

Networks this user agent came from. The operator publishes no ranges or hostnames, so other clients using its name may be among them:

- AS16509 Amazon.com, Inc.: `2a05:d01c:76e::/48`

## Hyperwatch

`@hyperwatch/useragent` returns the family `ClatterLabsSearchBot`. `src/modules/identity.js` has no
rule for it, so it gets no identity.

## Misc

- On the check date `clatterai.com` redirected to `www.clatterai.com`, which had no DNS address, so
  the site could not be read.
- Web searches for the name found no documentation or third-party profile.

## Sources

- https://www.clatterai.com (checked 2026-10-15, no DNS address)
- https://clatterai.com (checked 2026-10-15, redirects to https://www.clatterai.com/)
