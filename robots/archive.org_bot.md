---
name: archive.org_bot
operator: Internet Archive
website: https://archive.org
documentation: https://archive.org/details/archive.org_bot
category: archive
robots_txt_token: archive.org_bot
respects_robots_txt: partial
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: archive.org bot
  identity: Archive.org
last_checked: 2026-10-15
---

# archive.org_bot

## Description

archive.org_bot is the crawler the Internet Archive uses for its "wide crawl of the web", whose
captures are served by the Wayback Machine. This file also covers `special_archiver`, used by
Archive-It, the Internet Archive's web archiving service for institutions, on sites exempted from
its `robots.txt` policy.

## Behavior

The Internet Archive says it tries "to crawl at a pace slow enough to not disrupt normal web
activity". It does not archive pages that require a password, pages only reachable by submitting a
form, or "pages on secure servers". Crawl rate, JavaScript rendering and `Crawl-delay` support are
not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; archive.org_bot +http://archive.org/details/archive.org_bot) Zeno/7d76126 warc/v0.8.102
Mozilla/5.0 (compatible; special_archiver; Archive-It; +http://archive-it.org/files/site-owners-special.html)
```

The Internet Archive gives only the token `archive.org_bot`. Both full strings come from Known
Agents. The URL in the second one is Archive-It's page for site owners.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

```
User-agent: archive.org_bot
Disallow: /
```

The Internet Archive's help pages say pages "may not be archived due to robots exclusions". In
2017 it announced it had stopped following `robots.txt` on U.S. government and military sites and
was looking to do so "more broadly". It does not document its current policy. Archive-It says its
crawls "in general" respect `robots.txt`, but `special_archiver` is used on sites that have been
exempted from that policy. Exclusion from the Wayback Machine can be requested from
info@archive.org.

## IP ranges and verification

None published. No hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` parses the first string as family `archive.org bot` and the second as
`special archiver`. For both, Hyperwatch sets the identity `Archive.org` when the reverse DNS name
ends with `.archive.org`. A fallback also sets `Archive.org` for any user agent when the name ends
with `.us.archive.org`. Neither check uses a forward lookup, so whoever controls an address's
reverse DNS can pass them. The Internet Archive does not document these hostnames.

## Misc

Problems with the crawler can be reported to the address shown as an image on the
archive.org_bot page (bot at archive dot org). Archive-It questions go to
archive-itfeedback@archive.org.

## Sources

- https://archive.org/details/archive.org_bot (checked 2026-10-15, through https://archive.org/metadata/archive.org_bot)
- https://help.archive.org/help/wayback-machine-general-information/ (checked 2026-10-15)
- https://help.archive.org/help/how-do-i-request-to-remove-something-from-archive-org/ (checked 2026-10-15)
- https://blog.archive.org/2017/04/17/robots-txt-meant-for-search-engines-dont-work-well-for-web-archives/ (checked 2026-10-15)
- https://archive-it.org/files/site-owners-special.html (checked 2026-10-15)
- https://knownagents.com/agents/archive-org-bot (checked 2026-10-15)
- https://knownagents.com/agents/special-archiver (checked 2026-10-15)
