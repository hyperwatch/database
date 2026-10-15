---
name: github-camo
operator: GitHub
website: https://github.com
documentation: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-anonymized-urls
category: other
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: github-camo
  identity: GitHub Camo
last_checked: 2026-10-15
---

# github-camo

## Description

github-camo is the image proxy GitHub runs on Camo, an open-source project. When Markdown on GitHub
(a README, an issue, a comment) shows an image from another site, GitHub rewrites the image address
to a Camo URL, and Camo fetches the image from the site.

## Behavior

GitHub says Camo gives each image an anonymous proxy URL, so the viewer's browser details are not
passed to the site hosting the image. Its 2014 blog post says this started with non-HTTPS images and
was extended to HTTPS images.

GitHub documents two things for site owners: images must have a `Content-Type` that Camo supports,
and an image that changes should be served with `Cache-Control: no-cache`. A cached image can be
purged with `curl -X PURGE` on its Camo URL. Images on private networks or behind authentication
cannot be shown.

The archived Camo repository documents its defaults: at most 4 redirects, a 10-second timeout and
a 5 MiB size limit. GitHub does not say which values it uses in production.

## User agents

GitHub does not document the user agent. The open-source Camo sends `Camo Asset Proxy <version>`
in both `User-Agent` and `Via` unless `CAMO_HEADER_VIA` sets another value. The `github-camo` name
is not documented by GitHub.

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

GitHub does not say whether Camo reads `robots.txt`. As a proxy fetching images on behalf of page
viewers, no `robots.txt` token is documented.

## IP ranges and verification

None published for Camo. GitHub publishes the ranges of its services at
https://api.github.com/meta (JSON, one array per service: `hooks`, `web`, `api`, `git`, `pages`,
`packages`, `importer`, `github_enterprise_importer`, `copilot`, `actions`, `codespaces` and
others, with no date in the file). None of the arrays is named for Camo.

## Hyperwatch

`@hyperwatch/useragent` returns the family `github-camo` for user agents starting with
`github-camo`, and `Camo Asset Proxy` for the open-source default. `src/modules/identity.js` sets
the identity `GitHub Camo` for the family `github-camo` when the address is in
`src/data/github-ips.json` (published list: the `hooks`, `web`, `api`, `git`, `pages`, `packages`,
`importer`, `github_enterprise_importer` and `copilot` ranges of `api.github.com/meta`, 136
prefixes, refreshed with `node scripts/fetch-github-ips.js`) or in the inline range
`9.234.0.0/17`.

Where it falls short:

- GitHub does not say that Camo fetches from these ranges: the choice of arrays is Hyperwatch's own.
- `9.234.0.0/17` is listed by GitHub under `actions`. Actions runners there run any GitHub user's
  workflows, which can send the same user agent.
- On 2026-10-15 `api.github.com/meta` listed 139 prefixes under those arrays: the 3 new ones are
  `hooks` ranges inside `9.234.0.0/17`, so already accepted.

## Misc

- The Camo repository (github.com/atmos/camo) was archived on 2021-04-07.

## Sources

- https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-anonymized-urls (checked 2026-10-15)
- https://github.blog/news-insights/product-news/proxying-user-images (checked 2026-10-15)
- https://github.com/atmos/camo (checked 2026-10-15)
- https://api.github.com/meta (checked 2026-10-15)
