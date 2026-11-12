---
name: SubstackContentFetch
operator: Substack
website: https://substack.com
documentation: null
category: unknown
robots_txt_token: SubstackContentFetch
respects_robots_txt: unknown
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: SubstackContentFetch
  identity: Substack
last_checked: 2026-11-12
---

# SubstackContentFetch

## Description

SubstackContentFetch points to `https://substack.com/` in its user agent, and Substack, the
newsletter and publishing platform, serves the key directory its requests are signed with (see
"IP ranges and verification"). Substack publishes no page describing the robot: a search of
substack.com and support.substack.com on 2026-11-12 found none. According to Known Agents, it
fetches external pages to generate link previews, embed content or gather information for
newsletters, is triggered by a shared link, and usually makes a single request shortly after a link
is shared.

## Behavior

Not documented by Substack.

## User agents

Not documented by Substack. According to Known Agents, the strings seen most often are:

```
SubstackContentFetch/1.0 (https://substack.com/)
SubstackContentFetch/1.0 (https://substack.com/) facebookexternalhit/1.1 Facebot Twitterbot/1.0
SubstackContentFetch/1.0 (https://substack.com/),gzip(gfe)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: SubstackContentFetch
Disallow: /
```

The token is the product name in the user agent. Whether the robot reads `robots.txt` is not
documented by Substack; Known Agents says it is not expected to follow it.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

Substack serves a Web Bot Auth key directory at
https://substack.com/.well-known/http-message-signatures-directory: on 2026-11-12 it held 1
`OKP` / `Ed25519` key without a `kid`, and the directory's own signature used the key's JWK
thumbprint as its `keyid`. Substack does not document which robots sign with it or the
`Signature-Agent` value they send; Hyperwatch lists `https://substack.com` as the agent for
SubstackContentFetch. Since the directory has no `kid`, a signature can only name the key by its
JWK thumbprint.

## Hyperwatch

`@hyperwatch/useragent` 4.1.0 returns the family `SubstackContentFetch` for the three strings above.
In Hyperwatch 5.6.0, `src/modules/identity.js` sets the identity `Substack` signed only: a verified
signature of `https://substack.com` (the `signedOnly` map, checked before the rules per family)
gives `Substack` whatever the user agent. `https://substack.com` is in
`src/data/webbotauth-agents.json`, so Hyperwatch fetches its key directory. There is no rule for the
family `SubstackContentFetch`: without the `webbotauth` module (off by default) or without a valid
signature, the robot gets no identity.

## Misc

Not documented.

## Sources

- https://substack.com/.well-known/http-message-signatures-directory (checked 2026-11-12)
- https://knownagents.com/agents/substackcontentfetch (checked 2026-11-12, third party)
