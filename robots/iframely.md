---
name: Iframely
operator: Itteco Software Corp. (Iframely)
website: https://iframely.com
documentation: https://iframely.com/docs/about
category: social-preview
robots_txt_token: null
respects_robots_txt: no
verification:
  method: both
  ip_list: https://iframely.com/ips-v4
  hostnames: [".iframely.com"]
hyperwatch:
  family: Iframely
  identity: Iframely
last_checked: 2026-11-19
---

# Iframely

## Description

Iframely is a software-as-a-service that generates URL previews and rich media embeds for social
apps and news publishers. Its Preview Agent fetches a URL when "a person shared that URL on an
application built by one of our customers", and returns its title, description, thumbnail and
similar metadata. Iframely says it acts on the customer's behalf, not on its own.

## Behavior

Iframely says the Preview Agent does not crawl or follow links: it takes a single URL as input. It
reads only the page's metadata (Open Graph, Twitter Cards, oEmbed, Google's structured data and
Iframely's own rich media discovery protocol), never the page body, and usually leaves the page as
soon as it has read the `<meta>` part. Images, videos and audio files referenced by those tags are
checked with HEAD requests or HTTP Range headers for the first few bytes. Thumbnails used in
Iframely's URL cards are fetched once and cached on its CDN.

An active URL may be re-fetched "as often as once per hour on their first day", tapering off to
about once a month as the content ages. Cached content is purged after three months of inactivity.

JavaScript rendering and `Crawl-delay` support are not documented.

## User agents

Exact strings, one per line:

```
Iframely/1.3.1 (+https://iframely.com/docs/about)
```

This is the documented string. Iframely says the version and an optional app name extension "may
and will change"; the extension, when present, names the customer who triggered the request, as
the customer entered it.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not possible: Iframely says "We don't consult your `robots.txt` for these requests", because the
Preview Agent only fetches the one URL a person shared. `robots.txt` applies to its Processing and
Training Agents (see [Misc](#misc)). No token is documented for the Preview Agent. Iframely offers
to add a site to its ignorelist on request (support@iframely.com).

## IP ranges and verification

Iframely documents three ways to verify its traffic, the same for its three agents:

- IP lists: https://iframely.com/ips-v4 and https://iframely.com/ips-v6, plain text, one prefix per
  line, "populated automatically from our internet gateways". On 2026-11-19 the IPv4 list held 26
  `/32` addresses and the IPv6 list one prefix, `2600:1f18:fde:7200::/56`. The lists give no
  generation date (the server's `Last-Modified` for the IPv4 list was 2025-05-13).
- Reverse DNS: "Iframely traffic resolves to a subdomain of iframely.com". Iframely says reverse
  DNS reliably verifies IPv4 traffic only. Whether the name resolves back to the address is not
  documented.
- Web Bot Auth: "All three Iframely agents sign their requests", with `Signature`,
  `Signature-Input` and `Signature-Agent` headers; "The signature host resolves to iframely.com".
  The exact `Signature-Agent` value is not documented. The key directory
  https://iframely.com/.well-known/http-message-signatures-directory held one `OKP` / `Ed25519` key
  without a `kid` on 2026-11-19, so a signature's `keyid` can only match the key's JWK thumbprint.
  The directory's own response was signed with that key, its `keyid` being the thumbprint. Iframely
  says some customers ask for their own signature to be used instead of Iframely's.

Every request also carries headers naming the customer behind it: `Forwarded: for=<customer>;
use=<use>` (RFC 7239), `X-Iframely-Request-ID`, `X-Iframely-App`, `X-Iframely-Customer: name=<name>;
url=<url>` (when provided), `X-Iframely-Processing: mode=<mode>; use=<use>` and
`X-Iframely-Contact`.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 parses the user agent as family `Iframely`. Since Hyperwatch 5.7.0,
`src/modules/identity.js` sets the identity `Iframely` signed only: a verified signature of
`https://iframely.com` (the `signedOnly` map, checked before the rules per family) gives `Iframely`
whatever the user agent, so it covers the Processing and Training Agents too when they sign with
that agent. `https://iframely.com` is in `src/data/webbotauth-agents.json` (robot `Iframely`), and
its one key is in `webbotauth-keys.json`, the same as the published directory on 2026-11-19.

This falls short of Iframely's documentation: there is no rule for the family `Iframely`, and
Hyperwatch uses neither the published IP lists nor the `iframely.com` hostnames. Without the
`webbotauth` module (off by default), without a valid signature, or for requests signed with a
customer's own key, the request gets no identity.

## Misc

Iframely runs two other agents, with their own pages and user agents, which check `robots.txt`
(RFC 9309) before fetching; no `robots.txt` token is documented for either:

- Processing Agent, for indexing, search and AI-assisted retrieval on a customer's behalf
  (https://iframely.com/docs/about-processing):
  `Iframely-Processing/1.3.1 (+https://iframely.com/docs/about-processing)`, family
  `Iframely-Processing`.
- Training Agent, for AI training and dataset use where the publisher permitted it
  (https://iframely.com/docs/about-training):
  `Iframely-Training/1.3.1 (+https://iframely.com/docs/about-training)`, family
  `Iframely-Training`.

Iframely is run by Itteco Software Corp. (copyright line of iframely.com). Contact:
support@iframely.com.

## Sources

- https://iframely.com/docs/about (checked 2026-11-19)
- https://iframely.com/docs/allowlisting (checked 2026-11-19)
- https://iframely.com/docs/about-processing (checked 2026-11-19)
- https://iframely.com/docs/about-training (checked 2026-11-19)
- https://iframely.com/ips-v4 (checked 2026-11-19)
- https://iframely.com/ips-v6 (checked 2026-11-19)
- https://iframely.com/.well-known/http-message-signatures-directory (checked 2026-11-19)
