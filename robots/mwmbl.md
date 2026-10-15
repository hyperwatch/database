---
name: mwmbl
operator: Mwmbl (open-source project; crawling done by volunteers)
website: https://mwmbl.org
documentation: https://github.com/mwmbl/mwmbl/blob/main/mwmbl/crawler/README.md
category: search-engine
robots_txt_token: mwmbl
respects_robots_txt: yes
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: mwmbl
  identity: null
last_checked: 2026-10-15
---

# mwmbl

## Description

Mwmbl is a non-profit, open-source search engine (AGPL) with no ads or tracking. The index is
central, but "the crawling is distributed across servers run by our volunteers". Each volunteer
runs the Mwmbl crawler (with Docker Compose) on their own machine, fetches batches of URLs given
by the central server and sends the results back. Requests with this user agent therefore come
from many unrelated people and networks.

## Behavior

From the crawler README and source code:

- It fetches HTML pages and extracts the title, main text and links. It skips binary files such as
  images and PDFs. It does not render JavaScript (it uses `requests` and the `justext` library).
- It checks `robots.txt` before fetching any URL, using Python's `urllib.robotparser`. A
  `robots.txt` that cannot be fetched, returns a status other than 200, or cannot be decoded is
  treated as allowing everything.
- `robots.txt` is cached for 24 hours (1 hour after an error).
- `Crawl-delay` is not read from `robots.txt`. Each operator sets a delay between URLs per thread
  (`CRAWL_DELAY_SECONDS`, default 0). Defaults are 2 processes of 20 threads. A batch holds at most
  one URL per domain.
- The request timeout is 3 seconds.

## User agents

Exact strings, one per line:

```
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact )
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact automation@protobit.io)
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact dev@agalmic.ltd)
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact mwmbl.smirk305@passinbox.com (Mwmbl Crawler Operator))
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact mwmbl@reannLegge.ca)
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact sub1882_mwmbl.org@eagal.org)
mwmbl/0.2.0 (https://github.com/mwmbl/mwmbl/ contact yasappopo@murena.io (Mwmbl Crawler Operator))
```

The template in the source is
`mwmbl/{CRAWLER_VERSION} (https://github.com/mwmbl/mwmbl/ contact {MWMBL_CONTACT_INFO})`.
`MWMBL_CONTACT_INFO` is required and is the contact (email or URL) of the volunteer running that
crawler, so the contact part differs per operator. It can be empty.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: mwmbl
Disallow: /
```

Python's `robotparser` takes the part of the user agent before the first `/` (`mwmbl`) and matches
a group whose `User-agent` value is contained in it, case-insensitively. `User-agent: mwmbl` and
`*` both apply. `Crawl-delay` is ignored.

## IP ranges and verification

None published. Volunteers run the crawler on their own networks, so there is no IP list, reverse
DNS name or ASN.

## Hyperwatch

`@hyperwatch/useragent` returns the family `mwmbl`. `src/modules/identity.js` has no rule for it,
so Hyperwatch sets no identity. With no possible verification, this is expected.

## Misc

- Mwmbl also has a Firefox extension that fetches results from commercial search engines to
  evaluate Mwmbl's ranking. That is separate from the crawler.
- Crawling gives more weight to sites that the community champions.

## Sources

- https://github.com/mwmbl/mwmbl (checked 2026-10-15)
- https://github.com/mwmbl/mwmbl/blob/main/mwmbl/crawler/README.md (checked 2026-10-15)
- https://github.com/mwmbl/mwmbl/blob/main/mwmbl/crawler/retrieve.py (checked 2026-10-15)
- https://book.mwmbl.org/ (checked 2026-10-15)
