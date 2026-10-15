---
name: GoogleImageProxy
operator: Google
website: https://mail.google.com
documentation: https://knowledge.workspace.google.com/admin/gmail/advanced/set-up-an-image-url-proxy-allowlist
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: GoogleImageProxy
  identity: Google
last_checked: 2026-10-15
---

# GoogleImageProxy

## Description

GoogleImageProxy is the user agent of Gmail's image proxy. Google says that "when your users open
email messages, Gmail uses Google's secure proxy servers to serve images that might be included in
these messages". Each request follows a Gmail user opening a message, so the proxy fetches images
for people reading their mail, not to crawl.

## Behavior

From Gmail's help: Google scans images before users receive them, so that "senders can't use image
loading to get information about your computer or location" and can't set or read cookies. Images
from senders or messages Gmail finds suspicious are not loaded automatically. Workspace
administrators can list internal image URLs that bypass the proxy.

Google does not document the user agent, request rate or caching.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (Windows NT 5.1; rv:11.0) Gecko Firefox/11.0 (via ggpht.com GoogleImageProxy)
```

This string comes from third parties (ScientiaMobile in 2018, Known Agents), not from Google.
ScientiaMobile says the proxy replaces the reader's user agent with its own.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented. Google gives no token for the image proxy and does not say whether it reads
`robots.txt`. Blocking it would stop images from loading for Gmail users.

## IP ranges and verification

None published for this user agent. Google's crawler documentation does not list the Gmail image
proxy, so its user-triggered fetcher lists and reverse DNS names (`google-proxy-*.google.com`,
`*.gae.googleusercontent.com`) are not documented as applying to it.

## Hyperwatch

`@hyperwatch/useragent` returns the family `GoogleImageProxy` for the string above. In
`src/modules/identity.js`, Hyperwatch sets the identity `Google` for the families `Google`,
`GoogleDocs`, `docs.google.com`, `Google Favicon` and `GoogleImageProxy` when the reverse DNS
hostname (not forward-confirmed) ends with `.google.com`. It uses no address list for them.

## Misc

- The parser has a rule mapping `via ggpht.com GoogleImageProxy` to a family `GmailImageProxy`,
  but an earlier rule matches first and returns `GoogleImageProxy`.
- Other Google fetchers that Hyperwatch identifies as `Google`: Google Favicon and GoogleDocs.

## Sources

- https://knowledge.workspace.google.com/admin/gmail/advanced/set-up-an-image-url-proxy-allowlist (checked 2026-10-15, redirected from https://support.google.com/a/answer/3299041)
- https://support.google.com/mail/answer/145919 (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/google-user-triggered-fetchers (checked 2026-10-15)
- https://www-2018.scientiamobile.com/?p=20076 (checked 2026-10-15)
- https://knownagents.com/agents/googleimageproxy (checked 2026-10-15)
