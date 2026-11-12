---
name: ExaSearchBot-Images
operator: Exa
website: https://exa.ai
documentation: https://images.crawler.exa.ai/
category: ai-search
robots_txt_token: ExaSearchBot-Images
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: ExaSearchBot-Images
  identity: Exa
last_checked: 2026-11-12
---

# ExaSearchBot-Images

## Description

ExaSearchBot-Images is the robot Exa uses to fetch the images that appear on pages
[ExaSearchBot](exasearchbot.md) has crawled, so that search results can show them.

## Behavior

Each image is a single `GET` for the image URL, reduced to at most 560 pixels on its longest side
for display as a thumbnail. Exa says it is rate-limited per host (no number given), fetches images
only, does not try to bypass logins, paywalls or CAPTCHAs and submits no forms.

Exa says each request has an `Accept` header listing image types and a `Referer` set to the origin
of a page showing the image, or to the image's own origin.

How long `robots.txt` is cached is not documented.

## User agents

Exact strings, one per line:

```
ExaSearchBot-Images
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: ExaSearchBot-Images
Disallow: /
```

It applies the `robots.txt` of the host serving the image, which may differ from the host of the
page showing it. It looks for a group addressed to `ExaSearchBot-Images`, then the
`ExaSearchBot` group, then the rules set for major search engines, then `*`. A group for
`ExaSearchBot` therefore also covers its images unless `ExaSearchBot-Images` has its own.

## IP ranges and verification

None published. Exa says ExaSearchBot-Images does not fetch from the same addresses as
ExaSearchBot, and that verification does not depend on the address.

Requests are signed with HTTP Message Signatures (RFC 9421) following Web Bot Auth, with Ed25519
keys, and carry `Signature`, `Signature-Input` and `Signature-Agent` headers. The keys are at
https://images.crawler.exa.ai/.well-known/http-message-signatures-directory, a directory separate
from ExaSearchBot's: on 2026-11-12 it held one `OKP` / `Ed25519` key, whose `kid` is its JWK
thumbprint, so a signature's `keyid` finds it either way. Exa's page says the `Signature-Agent`
header identifies Exa without giving the value; Hyperwatch expects
`"https://images.crawler.exa.ai"`. No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `ExaSearchBot-Images`. In Hyperwatch 5.6.0,
`src/modules/identity.js` first sets the identity `Exa` on a verified signature of ExaUser's
`https://exauser.crawler.exa.ai`, whatever the user agent ("signed only"). For the family
`ExaSearchBot-Images`, it then sets `Exa` on a verified signature of `https://images.crawler.exa.ai`
when the `webbotauth` module is active (it is off by default); then only the signature counts.
Without the module, it checks the header only: `Signature-Agent` must contain
`"https://images.crawler.exa.ai"`, quotes included, and the signature is not validated against the
key directory.

## Misc

Images Exa fetches on a user's request, rather than by crawling, go out as `ExaUser-Images`. Exa's
page links to it but gives no details; Hyperwatch has no rule for it.

Contact: support@exa.ai, preferably from an address on the domain concerned.

## Sources

- https://images.crawler.exa.ai/ (checked 2026-11-10)
- https://crawler.exa.ai/ (checked 2026-11-10)
- https://images.crawler.exa.ai/.well-known/http-message-signatures-directory (checked 2026-11-12)
