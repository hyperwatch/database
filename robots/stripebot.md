---
name: Stripebot
operator: Stripe
website: https://stripe.com
documentation: https://docs.stripe.com/stripebot-crawler
category: other
robots_txt_token: Stripebot
respects_robots_txt: yes
verification:
  method: reverse-dns
  ip_list: null
  hostnames:
    - .crawl.stripe.com
hyperwatch:
  family: Stripebot
  identity: Stripe
last_checked: 2026-10-15
---

# Stripebot

## Description

Stripebot is Stripe's web crawler. It collects data from the websites of Stripe's users, which
Stripe uses to provide its services and to comply with financial regulations.

## Behavior

Stripe says Stripebot uses algorithms to minimize traffic, so that it does not affect the speed or
availability of its users' sites. Crawl rate, JavaScript rendering and `Crawl-delay` are not
documented.

## User agents

Stripe documents the format, with versions left out:

```
Mozilla/5.0 (X11; Linux {version}) AppleWebKit/{version} (KHTML, like Gecko) Chrome/{version} Safari/{version} (Stripebot/{version}; +https://docs.stripe.com/stripebot-crawler)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Stripebot
Disallow: /
```

Stripe says Stripebot "mostly follows" RFC 9309. It reads `User-Agent`, `Allow` and `Disallow`
lines (case-insensitive). It follows the first group whose `User-Agent` is `Stripebot`, or else the
first `*` group, and ignores later matching groups. After a change to `robots.txt` it may keep
using a cached copy for a while, and it may use a cached copy when reading the file fails.

## IP ranges and verification

Stripe recommends a forward-confirmed reverse DNS check: the address must resolve to a name in
`crawl.stripe.com` (for example `1-2-3-4.crawl.stripe.com`), and that name must resolve back to the
same address. No IP list or ASN is published.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Stripebot`. `src/modules/identity.js` sets the identity
`Stripe` when the reverse DNS hostname ends with `.stripe.com`. It reads the unconfirmed hostname,
not the forward-confirmed one, and accepts any name under `stripe.com`, not only
`crawl.stripe.com`.

## Misc

- Stripe's webhook requests (`Stripe/1.0 (+https://stripe.com/docs/webhooks)`, family `Stripe`)
  are not a robot. Hyperwatch gives them the same identity under the same rule.
- Contact: stripebot@stripe.com.

## Sources

- https://docs.stripe.com/stripebot-crawler (checked 2026-10-15)
