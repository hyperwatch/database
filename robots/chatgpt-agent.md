---
name: ChatGPT Agent
operator: OpenAI
website: https://openai.com
documentation: https://help.openai.com/en/articles/11845367-chatgpt-works-cloud-browser-allowlisting
category: ai-assistant
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: Chrome
  identity: ChatGPT Agent
last_checked: 2026-11-12
---

# ChatGPT Agent

## Description

ChatGPT Agent is the remote browser OpenAI runs for tasks that users of ChatGPT delegate to it. It
has no user agent token of its own, so this file is named after what the CDNs and Hyperwatch call
it. The former URL of OpenAI's allowlisting article ends with `chatgpt-agent-allowlisting` and
redirects to an article titled "ChatGPT Work's Cloud browser allowlisting": OpenAI now calls the
product "Cloud browser". The same article says Akamai,
HUMAN and Vercel list this traffic under the existing bot name "ChatGPT Agent" (Vercel as
`chatgpt-operator`), and Cloudflare under the bot tag `chatgpt-agent`.

## Behavior

OpenAI says Cloud browser "gives ChatGPT Work its own browser on a separate computer in the cloud".
It reads pages, clicks buttons, fills in forms and carries out steps on public and signed-in
websites, and can keep working after the user has left the conversation. By default it asks the
user before visiting a new website, and asks for confirmation before actions such as a booking or a
payment. The user signs in to websites through a secure form; the browser keeps its own cookies and
sessions, separate from the user's own browser. The allowlisting article says that "at launch" it
could not sign in to websites or complete payments; the newer help article describes signing in.

Crawl rate, JavaScript rendering, `Crawl-delay` support and `robots.txt` handling are not
documented.

## User agents

Not documented: OpenAI publishes no user agent for Cloud browser. The user agents below were seen
on requests whose signature Hyperwatch verified (see [Observed HTTP headers](#observed-http-headers)):

```
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/156.0.0.0 Safari/537.36
curl/8.14.1
Mozilla/5.0
Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 Chrome/131.0.0.0 Safari/537.36
```

The first is the user agent of a desktop Chrome on Linux, as sent by any such browser: only the
signature tells the agent apart.

## Observed HTTP headers

Based on dozens of requests seen on 2026-11-12, verified as ChatGPT Agent by Hyperwatch 5.6.0: mostly
image requests made while showing pages of other sites (with the Chrome user agent), a few page
requests, and `POST` requests with a JSON body (with the `curl` user agent).

| Header | Values (share of requests) |
|---|---|
| `accept` | `image/jxl,image/avif,image/webp,image/apng,image/svg+xml,image/*,*/*;q=0.8` (79%), `*/*` (16%) |
| `accept-language` | `en-US` (79%), `en-US,en;q=0.9` (5%) |
| `content-type` | `application/json` (16%) |
| `priority` | `i` (79%) |
| `referer` | `(present)` (79%) |
| `sec-fetch-dest` | `empty` (79%) |
| `sec-fetch-mode` | `no-cors` (79%) |
| `sec-fetch-site` | `cross-site` (79%) |
| `signature` | `(present)` (100%) |
| `signature-agent` | `"https://chatgpt.com"` (100%) |
| `signature-input` | `(present)` (100%) |

No `sec-ch-ua` or other client hints were sent. The signatures cover `@authority`, `@method` and
`signature-agent`, with `tag="web-bot-auth"`, `alg="ed25519"` and a nonce.

## Blocking with robots.txt

Not documented: OpenAI names no `robots.txt` token for Cloud browser and does not say whether it
reads `robots.txt`. OpenAI says each website decides whether to allow its traffic, through its CDN
or firewall.

## IP ranges and verification

None published. OpenAI says requests are signed with HTTP Message Signatures (RFC 9421) and carry
`Signature`, `Signature-Input` and `Signature-Agent` headers, the last set to
`"https://chatgpt.com"`, and that sites should check that value "including the quotation marks"
before verifying the signature. The public keys are at
https://chatgpt.com/.well-known/http-message-signatures-directory: on 2026-11-12 it held one
`OKP` / `Ed25519` key, with `nbf` and `exp` fields (the key expires on 2026-11-19). Its `kid` is the
key's JWK thumbprint, and the `keyid` of the signatures seen is that thumbprint. No reverse DNS
hostnames or ASN are documented.

### Observed

Requests verified as ChatGPT Agent seen on 2026-11-12. The operator publishes no ranges or
hostnames.

Networks:

- AS13335 Cloudflare, Inc.: `2a13:9500:1e4::/48`

## Hyperwatch

`@hyperwatch/useragent` returns the family `Chrome` for the Chrome user agent above, `curl` for
`curl/8.14.1`, `Mozilla` for `Mozilla/5.0` and `AppleWebKit` for the Chrome/131 string without
`KHTML`. In Hyperwatch 5.6.0, `src/modules/identity.js` sets the identity `ChatGPT Agent` on a
verified signature of `https://chatgpt.com`, whatever the user agent ("signed only", the
`signedOnly` map, checked before the rules per family). `https://chatgpt.com` is in
`src/data/webbotauth-agents.json`, and its one key is in `webbotauth-keys.json`, the same as the
published directory on 2026-11-12. This needs the `webbotauth` module, off by default; without it,
Hyperwatch gives these requests no identity.

## Misc

- [ChatGPT-User](chatgpt-user.md) is OpenAI's fetcher for user actions in ChatGPT, with its own
  token and IP list.
- OpenAI distinguishes Cloud browser from the built-in browser of the ChatGPT desktop app, which runs
  on the user's computer.

## Sources

- https://help.openai.com/en/articles/11845367-chatgpt-works-cloud-browser-allowlisting (checked 2026-11-12)
- https://help.openai.com/en/articles/20001280-using-cloud-browser-in-chatgpt (checked 2026-11-12)
- https://chatgpt.com/.well-known/http-message-signatures-directory (checked 2026-11-12)
