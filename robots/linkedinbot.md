---
name: LinkedInBot
operator: LinkedIn
website: https://www.linkedin.com
documentation: https://www.linkedin.com/help/linkedin/answer/a521928
category: social-preview
robots_txt_token: LinkedInBot
respects_robots_txt: unknown
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: LinkedInBot
  identity: LinkedIn
last_checked: 2026-10-15
---

# LinkedInBot

## Description

LinkedInBot is LinkedIn's link preview fetcher. When a URL is shared on LinkedIn, it fetches the
page to read the Open Graph tags (`og:title`, `og:image`, `og:description`, `og:url`) and build the
preview card.

## Behavior

LinkedIn's help page "Make your website shareable on LinkedIn" covers the required tags and image
sizes but does not describe the robot itself. Crawl rate, JavaScript rendering, `Crawl-delay`
support and `robots.txt` caching are not documented.

## User agents

Exact strings, one per line:

```
LinkedInBot/1.0 (compatible; Mozilla/5.0; Apache-HttpClient +http://www.linkedin.com)
```

LinkedIn does not document its user agents.

## Observed HTTP headers

<!-- observed headers: to be filled -->

## Blocking with robots.txt

```
User-agent: LinkedInBot
Disallow: /
```

LinkedIn does not state whether LinkedInBot follows `robots.txt`. LinkedIn's own `robots.txt` uses
the token `LinkedInBot` (with `Allow: /`). Blocking it stops link previews on LinkedIn.

## IP ranges and verification

None published. LinkedIn documents no IP list, reverse DNS hostname or ASN for LinkedInBot.

## Hyperwatch

`@hyperwatch/useragent` returns the family `LinkedInBot`. `src/modules/identity.js` sets the
identity `LinkedIn` when the reverse DNS hostname of the address ends with `.linkedin.com`. This rule
reads the reverse DNS hostname, not the forward-confirmed one. The suffix is Hyperwatch's own rule,
not documented by LinkedIn.

## Misc

- LinkedIn has a Post Inspector tool (https://www.linkedin.com/post-inspector/) for checking the
  preview of a URL.

## Sources

- https://www.linkedin.com/help/linkedin/answer/a521928 (checked 2026-10-15)
- https://www.linkedin.com/robots.txt (checked 2026-10-15)
- https://www.linkedin.com/post-inspector/ (checked 2026-10-15)
- https://chrisleverseo.com/user-agents/linkedinbot/ (checked 2026-10-15)
