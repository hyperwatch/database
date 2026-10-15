---
name: heritrix (Image-Meta)
operator: Erie Data Systems, LLC
website: https://www.image-meta.com
documentation: null
category: search-engine
robots_txt_token: null
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: www.image-meta.com
  identity: null
last_checked: 2026-10-15
---

# heritrix (Image-Meta)

## Description

This robot is a Heritrix crawler whose user agent points to image-meta.com. Image-Meta is a search
engine for image metadata, owned by Erie Data Systems, LLC (Erie, Pennsylvania, United States). It
indexes the EXIF, IPTC and XMP metadata of images that are publicly accessible on the web (device,
serial numbers, GPS coordinates, timestamps, authorship, copyright) and makes it searchable through
a web interface and an API.

Heritrix is the open-source web crawler of the Internet Archive.

## Behavior

Image-Meta does not document its crawler. Its about page says it indexes metadata only from images
that are already public, does not store original images, and may cache low-resolution thumbnails
temporarily for previews.

Heritrix's own documentation describes these settings, chosen by each operator:

- `robotsPolicyName`: `obey` (or `classic`) follows `robots.txt` and robots meta tags,
  `robotsTxtOnly` follows `robots.txt` only, `ignore` ignores both.
- Politeness: one URI per host at a time, with a delay set by `delayFactor`, `minDelayMs` and
  `maxDelayMs`.

Which settings Image-Meta uses is not documented. Crawl rate, `Crawl-delay`, JavaScript rendering
and `robots.txt` caching: not documented.

## User agents

Exact strings, one per line:

```
Mozilla/5.0 (compatible; heritrix/3.14.2-SNAPSHOT-2026-04-13T06:21:22Z +https://www.image-meta.com)
```

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

No token is documented by Image-Meta, and whether this crawler obeys `robots.txt` is not
documented. If it does, a `User-agent: *` group applies to it:

```
User-agent: *
Disallow: /
```

Image-Meta offers a data removal request page for people who want their data or images delisted:
https://image-meta.com/data-removal.

## IP ranges and verification

None published. No reverse DNS hostnames or ASN are documented.

## Hyperwatch

`@hyperwatch/useragent` returns the family `www.image-meta.com` (the host from the URL in the user
agent), not `heritrix`. `src/modules/identity.js` has no rule for it, so it gets no identity.

## Misc

The version in the user agent names a Heritrix 3.14.2 snapshot dated 2026-04-13. Image-Meta reports more than one billion indexed images.

## Sources

- https://www.image-meta.com (checked 2026-10-15)
- https://image-meta.com/about (checked 2026-10-15)
- https://heritrix.readthedocs.io/en/latest/ (checked 2026-10-15)
- https://heritrix.readthedocs.io/en/latest/configuring-jobs.html (checked 2026-10-15)
