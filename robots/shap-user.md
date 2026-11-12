---
name: Shap-User
operator: Parallel Web Systems
website: https://parallel.ai
documentation: https://parallel.ai/parallel-web-systems-bots
category: ai-assistant
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: Shap-User
  identity: Parallel
last_checked: 2026-11-12
---

# Shap-User

## Description

Shap-User is the user-triggered fetcher of Parallel Web Systems, which sells web search and
extraction APIs for AI agents. Parallel says it "identifies itself when accessing content on behalf
of users". Parallel's crawler is [ShapBot](shapbot.md).

## Behavior

Parallel says Shap-User "is not used for crawling the web in an automatic fashion". What it fetches
and when, crawl rate, `Crawl-delay` support and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 AppleWebKit/537.36 (KHTML, like Gecko); compatible; Shap-User/0.1.0
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented: Parallel names no `robots.txt` token for Shap-User. It says Shap-User "is intended
to provide visibility rather than to be managed through automated controls", and points to ShapBot
for controlling automated crawling:

```
User-agent: ShapBot
Disallow: /
```

## IP ranges and verification

None published: Parallel's IP list (`shapbot.json`) is for ShapBot only. Parallel says Shap-User
signs its requests with Web Bot Auth (HTTP Message Signatures), with public keys at
https://shap-user.parallel.ai/.well-known/http-message-signatures-directory: on 2026-11-12 it held
two `OKP` / `Ed25519` keys. Each key's `kid` is its JWK thumbprint, and the directory's own
signatures use that thumbprint as their `keyid`. The `Signature-Agent` value is not documented;
Hyperwatch expects `https://shap-user.parallel.ai`, the directory's origin. No reverse DNS hostnames
or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Shap-User`. In Hyperwatch 5.6.0,
`src/modules/identity.js` has no rule for this family: it sets the identity `Parallel` on a verified
signature of `https://shap-user.parallel.ai`, whatever the user agent ("signed only", the
`signedOnly` map, checked before the rules per family). `https://shap-user.parallel.ai` is in
`src/data/webbotauth-agents.json`, and its two keys are in `webbotauth-keys.json`, the same as the
published directory on 2026-11-12. This needs the `webbotauth` module, off by default; without it,
Hyperwatch gives Shap-User no identity. ShapBot's own rule (hostname, list, or a signature of
`https://shapbot.parallel.ai`) does not apply to Shap-User.

## Misc

- Parallel's contacts: support@parallel.ai for crawler issues (preferably from an address on the
  domain concerned), index@parallel.ai for content questions.
- https://docs.parallel.ai/resources/crawler covers ShapBot only and does not mention Shap-User.

## Sources

- https://parallel.ai/parallel-web-systems-bots (checked 2026-11-12)
- https://docs.parallel.ai/resources/crawler (checked 2026-11-12)
- https://shap-user.parallel.ai/.well-known/http-message-signatures-directory (checked 2026-11-12)
