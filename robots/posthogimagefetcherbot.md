---
name: PostHogImageFetcherBot
operator: PostHog
website: https://posthog.com
documentation: https://posthog.com/docs/ai-research/image-fetcher-bot
category: ai-training
robots_txt_token: PostHogImageFetcherBot
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: PostHogImageFetcherBot
  identity: PostHog
last_checked: 2026-11-12
---

# PostHogImageFetcherBot

## Description

PostHogImageFetcherBot is run by PostHog, a product analytics company. PostHog's session recordings
refer to images by URL instead of storing a copy. To use those recordings for AI training, PostHog
downloads the images they refer to, then passes them through the same redaction pipeline as the
rest of the recording ("Faces, text, and barcodes are removed before anything is stored").

## Behavior

PostHog says the robot only downloads images from sites where a PostHog customer records sessions,
and only for organizations whose data can be used to train PostHog's AI models. It does not crawl,
follow links or index anything: it requests the images a recording refers to and the files it
needs to decide whether it may fetch them (`robots.txt` and `/.well-known/tdmrep.json`). It
downloads each image once; PostHog's specification sets the default minimum interval between two
fetches of the same image URL to 30 days, and revalidates with `If-None-Match` or
`If-Modified-Since`.

From the specification (the README of the image fetch lane, which PostHog calls the public
specification of the robot):

- `robots.txt` and `tdmrep.json` are fetched before any image of an origin and cached for 24 hours.
  A 4xx other than 404 or 410 on them is treated as a disallow for the whole origin; a 429, 5xx or
  timeout as unreachable (the cached copy is used, or the origin is refused for an hour).
- Opt-out signals besides `robots.txt`: `X-Robots-Tag: noai` or `noimageai` in the image response,
  `Content-Signal: ai-train=no` in `robots.txt`, `Content-Usage: train-ai=n` in the image response
  or in `robots.txt`, `tdm-reservation: 1` in the image response or in `/.well-known/tdmrep.json`.
  Any one of them stops the fetch. `X-Robots-Tag: noindex` is ignored.
- Requests in flight are limited per registrable domain; a request rate per registrable domain is
  configurable and off by default. No numbers are given.
- It never sends cookies or credentials, and accepts `gzip`, `deflate`, `br` and `zstd`.

PostHog's documentation page says the robot sends no `Referer` header, while the specification says
every request sends `Referer: https://us.posthog.com/` (never the page that showed the image).

JavaScript rendering is not documented (it fetches images only).

## User agents

Exact strings, one per line:

```
PostHogImageFetcherBot/1.0 (+https://posthog.com/docs/ai-research/image-fetcher-bot)
```

This is the documented string. The specification says the user agent starts with
`PostHogImageFetcherBot` and contains a link to the documentation page.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: PostHogImageFetcherBot
Disallow: /
```

PostHog says the robot checks `robots.txt` before every fetch, so the change takes effect on its
next visit (the specification caches `robots.txt` for 24 hours). It follows `Crawl-delay` in its
group: it uses the longer of the site's value and its own interval, and the delay applies per
origin. Group selection uses a TypeScript port of Google's `robots.txt` parser (RFC 9309).

Blocking the user agent at a CDN or web server also works: PostHog says the robot treats the block
as final and stops requesting from the site. An opt-out applies to future fetches only: images
already downloaded are not deleted. Blocking the robot does not affect session recording.

## IP ranges and verification

None published. PostHog says the user agent is the way to identify the robot and does not publish
addresses "because the addresses can change"; it offers a stable range on request. No reverse DNS
hostnames or ASN are documented.

The specification says every request is signed with Web Bot Auth (RFC 9421), with `Signature`,
`Signature-Input` and `Signature-Agent` headers, tested against Cloudflare's implementation. The
`Signature-Agent` value is `"https://us.posthog.com"` (a quoted string, the legacy form Cloudflare
requires). The signature covers `@method`, `@authority`, `@target-uri` and `signature-agent`, with
`tag="web-bot-auth"`, `alg="ed25519"`, a nonce and `expires` 60 seconds after `created`; `keyid` is
the JWK thumbprint of the signing key. The key directory is
https://us.posthog.com/.well-known/http-message-signatures-directory: on 2026-11-12 it held 1
`OKP` / `Ed25519` key without a `kid`, and the directory's own signature used the key's JWK
thumbprint as its `keyid`.

## Hyperwatch

`@hyperwatch/useragent` 4.1.0 returns the family `PostHogImageFetcherBot`. In Hyperwatch 5.6.0,
`src/modules/identity.js` sets the identity `PostHog` signed only: a verified signature of
`https://us.posthog.com` (the `signedOnly` map, checked before the rules per family) gives `PostHog`
whatever the user agent. `https://us.posthog.com` is in `src/data/webbotauth-agents.json`, so
Hyperwatch fetches its key directory. There is no rule for the family `PostHogImageFetcherBot`:
without the `webbotauth` module (off by default) or without a valid signature, the robot gets no
identity.

## Misc

PostHog asks anyone who sees something in their logs that doesn't match its documentation to
contact it with the user agent and a timestamp.

## Sources

- https://posthog.com/docs/ai-research/image-fetcher-bot (checked 2026-11-12)
- https://github.com/PostHog/posthog/blob/master/nodejs/src/ingestion/pipelines/sessionreplay/ml-mirror-image-fetch/README.md (checked 2026-11-12)
- https://us.posthog.com/.well-known/http-message-signatures-directory (checked 2026-11-12)
