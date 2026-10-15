# Hyperwatch robot database

One Markdown file per robot (crawler, fetcher, link preview, monitoring agent) in
[`robots/`](robots/), describing who runs it, what it does, how it identifies itself, how to block it
with `robots.txt`, and how to verify that a request really comes from it.

Each file starts with YAML front matter for tools, followed by sections for people. See
[`TEMPLATE.md`](TEMPLATE.md).

## Front matter

| Field | Meaning |
|---|---|
| `name` | The robot's name, as in its user agent |
| `operator` | The company or project running it |
| `website`, `documentation` | Home page and robot documentation page |
| `category` | `search-engine`, `ai-training`, `ai-search`, `ai-assistant`, `seo`, `social-preview`, `archive`, `research`, `monitoring`, `marketing`, `other` or `unknown` |
| `robots_txt_token` | The `User-agent:` value it obeys in `robots.txt` |
| `respects_robots_txt` | What the operator states: `yes`, `partial`, `no` or `unknown` |
| `verification.method` | `ip-list`, `reverse-dns`, `both` or `none` |
| `verification.ip_list` | URL of the published address list, if any |
| `verification.hostnames` | Reverse DNS suffixes, if any |
| `hyperwatch.family` | Agent family returned by `@hyperwatch/useragent` |
| `hyperwatch.identity` | Identity set by Hyperwatch when the robot is verified, or `null` |
| `last_checked` | Date the sources were last checked |

## Rules

- Facts come from the operator's own pages when they exist, with the sources listed at the end of
  each file and the date they were checked.
- "Observed" sections only describe what robots send (user agents, headers). They never include
  the sites they were observed on, request counts or client addresses.
- An identity in Hyperwatch requires verification: a published IP list or reverse-confirmed DNS.
  A robot without either stays unverified here too.
