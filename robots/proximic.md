---
name: proximic
operator: Comscore, Inc.
website: https://www.comscore.com
documentation: https://www.comscore.com/Web-Crawler
category: marketing
robots_txt_token: proximic
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: proximic
  identity: Comscore
last_checked: 2026-11-19
---

# proximic

## Description

proximic is the crawler of Comscore's contextual content analysis (Proximic is a Comscore brand).
Comscore says the analysis "enables advertising partners to determine the best matching campaign
for a page's content": the crawler reports the page's language, content rating (G, PG13, R) and
IAB categories, and does not extract or store source code.

## Behavior

Comscore says the crawler visits a page "when an ad is about to be served", and that sites may also
be crawled "in a linear fashion" for site-level analysis requested by advertising partners. Visit
frequency depends on the type of content, its changes, the number of ad elements and other factors.

It only downloads the static, textual content, does not execute JavaScript to generate ad
impressions, honors `robots.txt` and crawls at a slow rate by default: "usually 1 request per
second". It follows `Crawl-Delay`. Changes to `robots.txt` may take up to a day to propagate.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; proximic; +https://www.comscore.com/Web-Crawler)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Comscore gives an example for one path:

```
User-agent: proximic
Disallow: /path/
```

and for the rate:

```
User-agent: proximic
Crawl-Delay: 2
```

("no more than 1 request per 2 seconds"). Blocking the whole site with `Disallow: /` is not given
as an example. No other token is documented.

## IP ranges and verification

None published: Comscore says "the IP addresses used by the crawler change from time to time". No
reverse DNS hostnames or ASN are documented. Comscore offers to add custom headers to its requests
to a site for allowlisting.

Web Bot Auth is not mentioned on Comscore's crawler page. The key directory
https://crawler-key.proximic.com/.well-known/http-message-signatures-directory held one `OKP` /
`Ed25519` key without a `kid` on 2026-11-19, so a signature's `keyid` can only match the key's JWK
thumbprint. The directory's own response was signed with that key, its `keyid` being the
thumbprint, and carried `Signature-Agent: "https://crawler-key.proximic.com"`. The
`Signature-Agent` value of the crawler's requests is not documented.

### Observed

Requests verified as Comscore with this user agent seen on 2026-11-25.
The operator publishes no ranges or hostnames.

Networks:

- AS14618 Amazon.com, Inc.: `3.85.80.0/24`, `54.167.210.0/24`, `3.84.129.0/24`, `100.30.179.0/24`

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 parses the user agent as family `proximic`. Since Hyperwatch 5.7.0,
`src/modules/identity.js` sets the identity `Comscore` signed only: a verified signature of
`https://crawler-key.proximic.com` (the `signedOnly` map, checked before the rules per family)
gives `Comscore` whatever the user agent. `https://crawler-key.proximic.com` is in
`src/data/webbotauth-agents.json` (robot `proximic`), and its one key is in `webbotauth-keys.json`,
the same as the published directory on 2026-11-19. There is no rule for the family `proximic`:
without the `webbotauth` module (off by default) or without a valid signature, the request gets no
identity. Comscore publishes no addresses or hostnames to check instead.

## Misc

- Contact: the Comscore contact form linked from the crawler page; no address is given.
- The identity is named after the operator (`Comscore`), not the robot.

## Sources

- https://www.comscore.com/Web-Crawler (checked 2026-11-19)
- https://crawler-key.proximic.com/.well-known/http-message-signatures-directory (checked 2026-11-19)
