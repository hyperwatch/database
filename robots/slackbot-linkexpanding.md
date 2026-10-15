---
name: Slackbot-LinkExpanding
operator: Slack
website: https://slack.com
documentation: https://api.slack.com/robots
category: social-preview
robots_txt_token: null
respects_robots_txt: no
verification:
  method: none
  ip_list: null
  hostnames: []
hyperwatch:
  family: Slackbot-LinkExpanding
  identity: Slack
last_checked: 2026-10-15
---

# Slackbot-LinkExpanding

## Description

Slackbot-LinkExpanding is Slack's link unfurling robot. When a link is posted in Slack, it fetches
the page to build the preview.

## Behavior

Slack says it requests only the start of the page, with HTTP `Range` headers, to read oEmbed,
Twitter Card and Open Graph tags. When those tags point to an image, video or audio file, it fetches
that file to check it and read its metadata. Responses are cached across Slack for about 30
minutes.

Slack says it treats its robots as acting for a person, not as crawlers. Redirect handling, size
limits and JavaScript rendering are not documented.

## User agents

Exact strings, one per line:

```
Slackbot-LinkExpanding 1.0 (+https://api.slack.com/robots)
```

## Observed HTTP headers

No requests from this robot were captured with their headers yet.

## Blocking with robots.txt

Slack says: "We do not currently honor `robots.txt` files." It offers to block embeds for a site on
request, through its contact form.

## IP ranges and verification

None published. Slack documents no IP list, reverse DNS hostname or ASN.

## Hyperwatch

`@hyperwatch/useragent` returns the family `Slackbot-LinkExpanding`. `src/modules/identity.js` sets
the identity `Slack` when the reverse DNS hostname ends with `.compute-1.amazonaws.com`. This is a
cloud hostname: any customer of AWS EC2 in us-east-1 passes it. Slack does not document where its
robots run.

## Misc

- Slack's other robots: `Slack-ImgProxy 0.19 (+https://api.slack.com/robots)` fetches and caches
  images posted in channels, and `Slackbot 1.0 (+https://api.slack.com/robots)` makes other
  requests (API calls to integrated services, outgoing webhooks). Hyperwatch parses them as
  `Slack-ImgProxy` and `Slackbot` and gives them no identity.

## Sources

- https://api.slack.com/robots (checked 2026-10-15)
