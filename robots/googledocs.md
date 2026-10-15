---
name: GoogleDocs
operator: Google
website: https://docs.google.com
documentation: null
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: GoogleDocs
  identity: Google
last_checked: 2026-10-15
---

# GoogleDocs

## Description

GoogleDocs is a user agent used by Google's Docs Editors (Docs, Sheets, Slides) when they fetch a
URL. Google does not document it: it is not in Google's list of crawlers and fetchers, and the help
pages of Sheets functions that fetch URLs (`IMPORTXML`, `IMPORTHTML`, `IMPORTFEED`, `IMPORTDATA`)
do not name a user agent. According to Known Agents, a third-party bot directory, it "visits URLs
referenced in Google Sheets and other Google Docs applications".

## Behavior

Not documented by Google. The Sheets help pages only say that `IMPORTXML` imports XML, HTML, CSV,
TSV, RSS and Atom data from a URL, and `IMPORTHTML` a table or list from an HTML page. Request rate,
caching and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; GoogleDocs; apps-spreadsheets; +http://docs.google.com)
```

This string comes from Known Agents, not from Google. The `apps-spreadsheets` part suggests Sheets;
other values are not documented.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Not documented. Google does not say whether these fetches read `robots.txt` or which token they
would obey. Known Agents says it is not expected to follow `robots.txt`. Google says its
user-triggered fetchers in general ignore `robots.txt`, but GoogleDocs is not on that list.

## IP ranges and verification

None published for this user agent. Google's general verification page lists, for its
user-triggered fetchers, the reverse DNS names `google-proxy-***-***-***-***.google.com` (addresses
in `user-triggered-fetchers-google.json`) and `***-***-***-***.gae.googleusercontent.com` (addresses
in `user-triggered-fetchers.json`), confirmed by a forward lookup. Google does not say whether the
Docs Editors fetch from these addresses.

## Hyperwatch

`@hyperwatch/useragent` returns the family `GoogleDocs` for the string above. In
`src/modules/identity.js`, Hyperwatch sets the identity `Google` for the families `Google`,
`GoogleDocs`, `docs.google.com` (described in the code as "how the parser reads the GoogleDocs
agent"), `Google Favicon` and `GoogleImageProxy` when the reverse DNS hostname (not
forward-confirmed) ends with `.google.com`. It uses no address list for them.

## Misc

- Other Google fetchers that Hyperwatch identifies as `Google`: Google Favicon and
  GoogleImageProxy.

## Sources

- https://developers.google.com/crawling/docs/crawlers-fetchers/overview-google-crawlers (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/google-user-triggered-fetchers (checked 2026-10-15)
- https://developers.google.com/crawling/docs/crawlers-fetchers/verify-google-requests (checked 2026-10-15)
- https://support.google.com/docs/answer/3093342 (checked 2026-10-15)
- https://support.google.com/docs/answer/3093339 (checked 2026-10-15)
- https://knownagents.com/agents/googledocs (checked 2026-10-15)
