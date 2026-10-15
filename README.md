# Hyperwatch robot database

One Markdown file per robot (crawler, fetcher, link preview, monitoring agent) in
[`robots/`](robots/), describing who runs it, what it does, how it identifies itself, how to block it
with `robots.txt`, and how to verify that a request really comes from it.

Each file starts with YAML front matter for tools, followed by sections for people. See
[`TEMPLATE.md`](TEMPLATE.md).

## Robots

| Robot | Operator | Category | Verification | Hyperwatch identity |
|---|---|---|---|---|
| [AmberAI-SourceReader](robots/amberai-sourcereader.md) | Unknown | unknown | none | - |
| [Applebot](robots/applebot.md) | Apple | search-engine | both | Applebot |
| [AwarioBot](robots/awariobot.md) | Awario | marketing | none | WebMeUp |
| [AzureAI-SearchBot](robots/azureai-searchbot.md) | Microsoft (by its name; not confirmed by Microsoft documentation) | unknown | none | - |
| [Barkrowler](robots/barkrowler.md) | Babbar.tech | seo | both | Babbar |
| [BelleaireCrawler](robots/belleairecrawler.md) | Unknown | unknown | none | - |
| [bingbot](robots/bingbot.md) | Microsoft | search-engine | both | Bing |
| [BitMoversBot](robots/bitmoversbot.md) | Byte Dev Limited | research | none | - |
| [Buck](robots/buck.md) | Hypefactors | marketing | none | - |
| [Bytespider](robots/bytespider.md) | ByteDance | unknown | none | Bytespider |
| [CCBot](robots/ccbot.md) | Common Crawl Foundation | archive | both | Common Crawl |
| [ChatGPT-User](robots/chatgpt-user.md) | OpenAI | ai-assistant | ip-list | ChatGPT |
| [ClatterLabsSearchBot](robots/clatterlabssearchbot.md) | Unknown | unknown | none | - |
| [Claude-SearchBot](robots/claude-searchbot.md) | Anthropic | ai-search | ip-list | Claude |
| [Claude-User](robots/claude-user.md) | Anthropic | ai-assistant | ip-list | Claude |
| [ClaudeBot](robots/claudebot.md) | Anthropic | ai-training | ip-list | Claude |
| [ClueWeb-Crawler](robots/clueweb-crawler.md) | Carnegie Mellon University (Language Technologies Institute) | research | none | - |
| [dksearch-bot](robots/dksearch-bot.md) | Unknown | research | none | - |
| [DuckAssistBot](robots/duckassistbot.md) | DuckDuckGo | ai-search | ip-list | - |
| [ExaSearchBot](robots/exasearchbot.md) | Exa | ai-search | web-bot-auth | Exa |
| [facebookexternalhit](robots/facebookexternalhit.md) | Meta | social-preview | ip-list | Facebook |
| [fyndbot](robots/fyndbot.md) | Fynd | search-engine | none | - |
| [Googlebot](robots/googlebot.md) | Google | search-engine | both | Googlebot |
| [GPTBot](robots/gptbot.md) | OpenAI | ai-training | ip-list | OpenAI GPTBot |
| [HaloBot](robots/halobot.md) | HaloScan | seo | ip-list | - |
| [HubSpot Crawler](robots/hubspot-crawler.md) | HubSpot | seo | ip-list | - |
| [ibou-search](robots/ibou-search.md) | ibou | search-engine | both | - |
| [IdarusBot](robots/idarusbot.md) | Idarus | search-engine | ip-list | - |
| [image-crawler](robots/image-crawler.md) | Unknown | unknown | none | - |
| [heritrix (Image-Meta)](robots/image-meta.md) | Erie Data Systems, LLC | search-engine | none | - |
| [JerryOSINT](robots/jerryosint.md) | unknown | research | none | - |
| [KeenableBot](robots/keenablebot.md) | Keenable.ai, Inc. | ai-search | ip-list | Keenable |
| [LinkedInBot](robots/linkedinbot.md) | LinkedIn | social-preview | none | LinkedIn |
| [LinkupBot](robots/linkupbot.md) | Linkup | ai-search | ip-list | Linkup |
| [MJ12bot](robots/mj12bot.md) | Majestic-12 Ltd | seo | none | Majestic |
| [MojeekBot](robots/mojeekbot.md) | Mojeek | search-engine | both | Mojeek |
| [mwmbl](robots/mwmbl.md) | Mwmbl (open-source project; crawling done by volunteers) | search-engine | none | - |
| [NagetBot](robots/nagetbot.md) | Naget | ai-search | none | - |
| [NumberLensBot](robots/numberlensbot.md) | unknown | unknown | none | - |
| [OAI-SearchBot](robots/oai-searchbot.md) | OpenAI | ai-search | ip-list | OpenAI SearchBot |
| [PerplexityBot](robots/perplexitybot.md) | Perplexity AI | ai-search | ip-list | Perplexity |
| [Reflectionbot](robots/reflectionbot.md) | Reflection AI | ai-training | both | Reflection |
| [SemanticScholarBot](robots/semanticscholarbot.md) | Allen Institute for AI (Ai2) | research | none | - |
| [SemrushBot](robots/semrushbot.md) | Semrush | seo | reverse-dns | Semrush |
| [SenderBot](robots/senderbot.md) | Sender Online Marketing GmbH | marketing | none | - |
| [SiteAuditBot](robots/siteauditbot.md) | Semrush | seo | both | Semrush |
| [TalarionSearchBot](robots/talarionsearchbot.md) | Talarion, Inc. | ai-search | none | - |
| [Twitterbot](robots/twitterbot.md) | X Corp. (formerly Twitter) | social-preview | both | Twitter |
| [VivianCrawler](robots/viviancrawler.md) | unknown | search-engine | none | - |
| [yacybot](robots/yacybot.md) | YaCy users (open-source peer-to-peer search engine project) | search-engine | none | - |
| [YandexBot](robots/yandexbot.md) | Yandex | search-engine | reverse-dns | Yandex |
| [YouBot](robots/youbot.md) | You.com | search-engine | both | You.com |

## Front matter

| Field | Meaning |
|---|---|
| `name` | The robot's name, as in its user agent |
| `operator` | The company or project running it |
| `website`, `documentation` | Home page and robot documentation page |
| `category` | `search-engine`, `ai-training`, `ai-search`, `ai-assistant`, `seo`, `social-preview`, `archive`, `research`, `monitoring`, `marketing`, `other` or `unknown` |
| `robots_txt_token` | The `User-agent:` value it obeys in `robots.txt` |
| `respects_robots_txt` | What the operator states: `yes`, `partial`, `no` or `unknown` |
| `verification.method` | `ip-list`, `reverse-dns`, `both`, `web-bot-auth` or `none` |
| `verification.ip_list` | URL of the published address list, if any |
| `verification.hostnames` | Reverse DNS suffixes, if any |
| `hyperwatch.family` | Agent family returned by `@hyperwatch/useragent` |
| `hyperwatch.identity` | Identity set by Hyperwatch when the robot is verified, or `null` |
| `last_checked` | Date the sources were last checked |

## Rules

- Facts come from the operator's own pages when they exist, with the sources listed at the end of
  each file and the date they were checked. What isn't documented says so.
- "Observed" parts describe what robots send and where they come from: user agents, HTTP headers,
  networks and reverse DNS hostnames. They never name the sites where they were observed, and never
  give request counts.
- Only the robot's own traffic is described. When it can be verified (published ranges, documented
  reverse DNS), requests that fail verification are left out: they come from other clients using its
  name.
- Observed networks are only listed for robots whose operator publishes no ranges, as prefixes
  (`/24` for IPv4, `/48` for IPv6) of hosting networks with their ASN. Access networks (ISPs,
  universities) are named, without prefixes. A user agent seen from many networks is described as
  reused, without a list.
- Observed reverse DNS hostnames are only listed when they differ from the documented ones, as
  patterns (`*.bc.googleusercontent.com`), with whether the name resolves back to the address
  (forward-confirmed).
- Observed headers come from requests the robot made itself. For a robot Hyperwatch can verify, only
  verified requests are counted. They were seen behind a CDN, which normalizes `accept-encoding` and
  adds conditional headers when revalidating its cache: those headers are left out.
- Verifying a robot means a published IP list, reverse DNS confirmed by a forward lookup, or a
  checked Web Bot Auth signature. The "Hyperwatch" section of each file says how Hyperwatch checks
  it today, including where it falls short of that.
