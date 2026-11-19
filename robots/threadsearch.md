---
name: threadsearch
operator: threadsearch
website: https://threadsearch.app
documentation: https://threadsearch.app/crawler
category: search-engine
robots_txt_token: threadsearch
respects_robots_txt: yes
verification:
  method: web-bot-auth
  ip_list: null
  hostnames: []
hyperwatch:
  family: threadsearch
  identity: threadsearch
last_checked: 2026-11-19
---

# threadsearch

## Description

threadsearch is the crawler of threadsearch, "a search engine where results carry discussion
threads" ("Web search with a discussion layer, ranked like a link aggregator"). Its crawler reads
pages that its discussions link to, so people can find them in search. threadsearch says the pages
are used to find them and to show their titles, short excerpts and links in its results, not to
train AI models or generate AI answers.

## Behavior

threadsearch says its crawler fetches:

- pages linked from posts on threadsearch, and pages linked from those pages' main text, a few steps
  out;
- new articles on sites it already reads: about once a day, the sitemaps listed in `robots.txt` (or
  `/sitemap.xml`) and the RSS or Atom feeds pages name, up to six files a visit, 10 seconds apart;
- a few sites in full: every page their sitemaps list, at most 600 queued every 6 hours;
- PDFs of up to 20 MB that pages link to or name with a `citation_pdf_url` tag.

It asks a site for at most one page every 10 seconds, or less often if `robots.txt` sets a
`Crawl-delay`. It revisits a page between once a week and twice a year, sends `If-None-Match` and
`If-Modified-Since` on revisits, reads `robots.txt` again each day, and backs off for up to 6 hours
after errors or `429`. It does not fetch login pages, images, archives, or links marked `nofollow`,
`sponsored` or `ugc`. Section fronts, indexes and home pages are read for their links only.

When a site answers `401`, `403` or `429`, it may take the page from Common Crawl's archive instead,
in a copy at most six months old, but only pages `robots.txt` lets it fetch for search.

JavaScript rendering is not documented.

## User agents

Exact strings, one per line:

```
threadsearch/0.1 (+https://threadsearch.app/crawler)
```

This is the documented string.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: threadsearch
Disallow: /
```

threadsearch also honors `Content-Signal` lines in `robots.txt`: with `search=no`, it does not crawl
the site and removes the pages it already has from search. Disallowing it or `search=no` also keeps
the site's pages out of what it takes from Common Crawl. It honors `noindex` and `nofollow` in a
robots meta tag or an `X-Robots-Tag` header.

## IP ranges and verification

None published. threadsearch says its requests are signed with Web Bot Auth (HTTP Message
Signatures), with `Signature-Agent: "https://threadsearch.app"`. The key directory is
https://threadsearch.app/.well-known/http-message-signatures-directory: on 2026-11-19 it held one
`OKP` / `Ed25519` key, without a `kid`, so a signature's `keyid` can only be the key's JWK
thumbprint. No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` 4.1.1 returns the family `threadsearch`. Since Hyperwatch 5.7.0 (checked on main at
736acaf), `src/modules/identity.js` sets the identity
`threadsearch` signed only: a verified signature of `https://threadsearch.app` (the `signedOnly`
map, checked before the rules per family) gives `threadsearch` whatever the user agent.
`https://threadsearch.app` is in `src/data/webbotauth-agents.json`, and its one key is in
`webbotauth-keys.json`, the same as the published directory on 2026-11-19. There is no rule for the
family `threadsearch`: without the `webbotauth` module (off by default) or without a valid
signature, the request gets no identity. This matches threadsearch's documentation, which publishes
no addresses or hostnames.

## Misc

- The crawler page is rendered with JavaScript; its text is in the page's script bundle.
- Contact: info@threadsearch.app.

## Sources

- https://threadsearch.app/crawler (checked 2026-11-19)
- https://threadsearch.app/.well-known/http-message-signatures-directory (checked 2026-11-19)
- https://threadsearch.app/ (checked 2026-11-19)
