---
name: Qwantbot
operator: Qwant
website: https://www.qwant.com
documentation: https://help.qwant.com/hc/en-us/articles/51146433634833-The-Qwant-bot-QwantBot-and-the-robots-txt-file
category: search-engine
robots_txt_token: Qwantbot
respects_robots_txt: yes
verification:
  method: both
  ip_list: https://help.qwant.com/qwantbot.json
  hostnames:
    - .qwant.com
hyperwatch:
  family: help.qwant.com
  identity: Qwant
last_checked: 2026-10-15
---

# Qwantbot

## Description

QwantBot is the crawler of Qwant, a French search engine. It crawls the web to build and refresh
the index behind Qwant search. A `Qwantbot-news` variant crawls for Qwant News.

## Behavior

Qwant says QwantBot adjusts its crawl frequency to the size and popularity of a site, and that a
valid sitemap and a fast server affect it. It supports `Crawl-delay` in seconds and the `noindex`
robots meta tag. JavaScript rendering and `robots.txt` caching are not documented.

## User agents

Qwant gives the general format
`Mozilla/5.0 (compatible; Qwantbot{-news}/X.Y_{worker_id}; +https://help.qwant.com/bot/)`, where
`-news` marks the Qwant News bot and `worker_id` the machine making the request. Its two examples:

```
Mozilla/5.0 (compatible; Qwantbot/1.0_12345; +https://help.qwant.com/bot/)
Mozilla/5.0 (compatible; Qwantbot-news/2.0; +https://help.qwant.com/bot/)
```

The constant element is the single word `Qwantbot`.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: Qwantbot
Disallow: /
```

`Crawl-delay` sets a minimum delay in seconds between two requests. A `robots.txt` file applies
only to its own host (`example.com`, not `blog.example.com`). Whether `Qwantbot-news` obeys a
separate token is not documented.

## IP ranges and verification

Qwant recommends a forward-confirmed reverse DNS check: the name must end in `qwant.com` (its
example is `qwantbot-1-162-242-91.qwant.com`) and must resolve back to the same address.

As an alternative, Qwant publishes https://help.qwant.com/qwantbot.json, an object with
`creationTimestampSecond` and a `prefixes` array of `{"ipv4Prefix": ...}` objects. On 2026-10-15 it
held 1 IPv4 prefix (`194.187.171.0/24`) and was dated 2025-11-26 (`1764143556`). The address in
Qwant's own reverse DNS example is not in that prefix. No ASN is documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `help.qwant.com` for the `Qwantbot` example and
`Qwantbot-news` for the news one.

`src/modules/identity.js` has a rule for the families `Qwantify` and `Qwantify-dev` (unconfirmed
hostname ending with `.qwant.com`), which the documented user agents don't produce. They get the
identity `Qwant` from the "Hostname only" fallback instead: any request, whatever its user agent,
whose unconfirmed hostname ends with `.qwant.com`. Qwant documents a forward-confirmed check; the
rule does not use the confirmed hostname, and the IP list is not used.

## Misc

`Qwantify` and `Qwantify-dev`, named in Hyperwatch's rule, are not mentioned on Qwant's current
page.

The page `https://help.qwant.com/bot/` (the URL in the user agent) redirects to the help article,
which returned a Cloudflare challenge to a script; its text was read through the help center's
API (`https://help.qwant.com/api/v2/help_center/en-us/articles/51146433634833.json`, updated
2026-10-09).

## Sources

- https://help.qwant.com/hc/en-us/articles/51146433634833-The-Qwant-bot-QwantBot-and-the-robots-txt-file (checked 2026-10-15)
- https://help.qwant.com/qwantbot.json (checked 2026-10-15)
