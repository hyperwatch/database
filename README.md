# Hyperwatch robot database

One Markdown file per robot (crawler, fetcher, link preview, monitoring agent) in
[`robots/`](robots/), describing who runs it, what it does, how it identifies itself, how to block it
with `robots.txt`, and how to verify that a request really comes from it.

Each file starts with YAML front matter for tools, followed by sections for people. See
[`TEMPLATE.md`](TEMPLATE.md).

[`identities.md`](identities.md) lists every identity Hyperwatch sets, how it checks it, and the robot
files it covers. [`AGENTS.md`](AGENTS.md) is the procedure
for adding or updating robots.

## Robots

| Robot | Operator | Category | Verification | Hyperwatch identity |
|---|---|---|---|---|
| [360Spider](robots/360spider.md) | 360 Search (Qihoo 360) | search-engine | ip-list | 360Spider |
| [AhrefsBot](robots/ahrefsbot.md) | Ahrefs | seo | both | Ahrefs |
| [AhrefsSiteAudit](robots/ahrefssiteaudit.md) | Ahrefs | seo | both | Ahrefs |
| [AIWebIndex](robots/aiwebindex.md) | Aleksma Ai, Inc. (Lyrenth) | ai-search | both | Lyrenth |
| [alexa site audit](robots/alexa-site-audit.md) | Alexa Internet (Amazon); service shut down | seo | none | Alexa |
| [AliyunSecBot](robots/aliyunsecbot.md) | Alibaba Cloud (by its user agent's contact address; not confirmed by Alibaba documentation) | other | none | AliyunSecBot |
| [amazon-Quick-on-behalf-of](robots/amazon-quick-on-behalf-of.md) | Amazon Web Services | other | ip-list | Amazon Quick |
| [Amazonbot](robots/amazonbot.md) | Amazon | ai-training | ip-list | Amazonbot |
| [AmberAI-SourceReader](robots/amberai-sourcereader.md) | Unknown | unknown | none | - |
| [Amzn-SearchBot](robots/amzn-searchbot.md) | Amazon | ai-search | ip-list | Amazon SearchBot |
| [Amzn-User](robots/amzn-user.md) | Amazon | ai-assistant | ip-list | Amazon User |
| [Applebot](robots/applebot.md) | Apple | search-engine | both | Applebot |
| [Aranet-SearchBot](robots/aranet-searchbot.md) | Unknown | unknown | none | Aranet |
| [archive.org_bot](robots/archive.org_bot.md) | Internet Archive | archive | none | Archive.org |
| [Arquivo-web-crawler](robots/arquivo-web-crawler.md) | Arquivo.pt (Portuguese Web Archive) | archive | ip-list | Arquivo |
| [AwarioBot](robots/awariobot.md) | Awario | marketing | none | WebMeUp |
| [AzureAI-SearchBot](robots/azureai-searchbot.md) | Microsoft (by its name; not confirmed by Microsoft documentation) | unknown | none | - |
| [Baiduspider](robots/baiduspider.md) | Baidu | search-engine | reverse-dns | Baidu |
| [Barkrowler](robots/barkrowler.md) | Babbar.tech | seo | both | Babbar |
| [BelleaireCrawler](robots/belleairecrawler.md) | Unknown | unknown | none | - |
| [bingbot](robots/bingbot.md) | Microsoft | search-engine | both | Bing |
| [BitMoversBot](robots/bitmoversbot.md) | Byte Dev Limited | research | none | - |
| [bl.uk_lddc_bot](robots/bl.uk_lddc_bot.md) | British Library (UK legal deposit libraries) | archive | none | British Library |
| [BLEXBot](robots/blexbot.md) | WebMeUp | seo | reverse-dns | WebMeUp |
| [BluechipBacklinks](robots/bluechipbacklinks.md) | Bluechip Backlinks | seo | none | Bluechip Backlinks |
| [bnf.fr_bot](robots/bnf.fr_bot.md) | Bibliothèque nationale de France (BnF) | archive | none | BnF.fr |
| [Buck](robots/buck.md) | Hypefactors | marketing | none | - |
| [Bytespider](robots/bytespider.md) | ByteDance | unknown | none | Bytespider |
| [CCBot](robots/ccbot.md) | Common Crawl Foundation | archive | both | Common Crawl |
| [ChatGPT-User](robots/chatgpt-user.md) | OpenAI | ai-assistant | ip-list | ChatGPT |
| [ClatterLabsSearchBot](robots/clatterlabssearchbot.md) | Unknown | unknown | none | - |
| [Claude-SearchBot](robots/claude-searchbot.md) | Anthropic | ai-search | ip-list | Claude |
| [Claude-User](robots/claude-user.md) | Anthropic | ai-assistant | ip-list | Claude |
| [ClaudeBot](robots/claudebot.md) | Anthropic | ai-training | ip-list | Claude |
| [Cliqzbot](robots/cliqzbot.md) | Cliqz GmbH (shut down in 2020) | search-engine | none | Cliqz |
| [ClueWeb-Crawler](robots/clueweb-crawler.md) | Carnegie Mellon University (Language Technologies Institute) | research | none | - |
| [coccocbot](robots/coccocbot.md) | Cốc Cốc Company Limited | search-engine | reverse-dns | Coc Coc |
| [DataForSeoBot](robots/dataforseobot.md) | DataForSEO | seo | both | DataForSeo |
| [Daum](robots/daum.md) | Kakao (Daum) | search-engine | ip-list | Daum |
| [Discordbot](robots/discordbot.md) | Discord | social-preview | ip-list | Discord |
| [dksearch-bot](robots/dksearch-bot.md) | Unknown | research | none | - |
| [DolfeEngineCrawler](robots/dolfeenginecrawler.md) | Unknown | unknown | none | Dolfe |
| [DotBot](robots/dotbot.md) | Moz | seo | none | Moz |
| [DuckAssistBot](robots/duckassistbot.md) | DuckDuckGo | ai-search | ip-list | DuckDuckGo |
| [DuckDuckBot](robots/duckduckbot.md) | DuckDuckGo | search-engine | ip-list | DuckDuckGo |
| [ev-crawler](robots/ev-crawler.md) | Headline | other | none | Headline |
| [ExaSearchBot](robots/exasearchbot.md) | Exa | ai-search | web-bot-auth | Exa |
| [facebookexternalhit](robots/facebookexternalhit.md) | Meta | social-preview | ip-list | Facebook |
| [FlipboardProxy](robots/flipboardproxy.md) | Flipboard | other | none | Flipboard |
| [fyndbot](robots/fyndbot.md) | Fynd | search-engine | none | - |
| [github-camo](robots/github-camo.md) | GitHub | other | none | GitHub Camo |
| [Google Favicon](robots/google-favicon.md) | Google | other | none | Google |
| [Googlebot](robots/googlebot.md) | Google | search-engine | both | Googlebot |
| [GoogleDocs](robots/googledocs.md) | Google | other | none | Google |
| [GoogleImageProxy](robots/googleimageproxy.md) | Google | other | none | Google |
| [GPTBot](robots/gptbot.md) | OpenAI | ai-training | ip-list | OpenAI GPTBot |
| [HaloBot](robots/halobot.md) | HaloScan | seo | ip-list | - |
| [HappyApps-WebCheck](robots/happyapps-webcheck.md) | Happy Apps, LLC | monitoring | none | Happy Apps |
| [heritrix (Image-Meta)](robots/image-meta.md) | Erie Data Systems, LLC | search-engine | none | - |
| [HubSpot Crawler](robots/hubspot-crawler.md) | HubSpot | seo | ip-list | - |
| [Hyperlink](robots/hyperlink.md) | Unknown | unknown | none | Meta |
| [ibou-search](robots/ibou-search.md) | ibou | search-engine | both | - |
| [IdarusBot](robots/idarusbot.md) | Idarus | search-engine | ip-list | - |
| [image-crawler](robots/image-crawler.md) | Unknown | unknown | none | - |
| [InfoTigerBot](robots/infotigerbot.md) | Infotiger UG (haftungsbeschränkt) | search-engine | reverse-dns | InfoTiger |
| [JerryOSINT](robots/jerryosint.md) | unknown | research | none | - |
| [Keenable-User](robots/keenable-user.md) | Keenable.ai, Inc. | ai-assistant | ip-list | Keenable |
| [KeenableBot](robots/keenablebot.md) | Keenable.ai, Inc. | ai-search | ip-list | Keenable |
| [Linespider](robots/linespider.md) | LINE | search-engine | none | Line |
| [LinkedInBot](robots/linkedinbot.md) | LinkedIn | social-preview | none | LinkedIn |
| [LinkupBot](robots/linkupbot.md) | Linkup | ai-search | ip-list | Linkup |
| [Mail.RU_Bot](robots/mail.ru_bot.md) | Mail.ru (by the link in its user agent; documentation not available) | unknown | none | Mail.RU |
| [MBCrawler](robots/mbcrawler.md) | Monitor Backlinks | seo | none | Monitor Backlinks |
| [MegaIndex.ru](robots/megaindex.ru.md) | MegaIndex | seo | none | MegaIndex.ru |
| [meta-externalagent](robots/meta-externalagent.md) | Meta | ai-training | ip-list | Meta |
| [meta-webindexer](robots/meta-webindexer.md) | Meta | ai-search | ip-list | Meta |
| [MJ12bot](robots/mj12bot.md) | Majestic-12 Ltd | seo | none | Majestic |
| [MojeekBot](robots/mojeekbot.md) | Mojeek | search-engine | both | Mojeek |
| [mwmbl](robots/mwmbl.md) | Mwmbl (open-source project; crawling done by volunteers) | search-engine | none | - |
| [NagetBot](robots/nagetbot.md) | Naget | ai-search | none | - |
| [Neevabot](robots/neevabot.md) | Neeva (shut down in 2023) | search-engine | none | Neevabot |
| [NumberLensBot](robots/numberlensbot.md) | unknown | unknown | none | - |
| [OAI-SearchBot](robots/oai-searchbot.md) | OpenAI | ai-search | ip-list | OpenAI SearchBot |
| [Perplexity-User](robots/perplexity-user.md) | Perplexity AI | ai-assistant | ip-list | Perplexity |
| [PerplexityBot](robots/perplexitybot.md) | Perplexity AI | ai-search | ip-list | Perplexity |
| [PetalBot](robots/petalbot.md) | Huawei (Petal Search) | search-engine | reverse-dns | PetalBot |
| [PingdomBot](robots/pingdombot.md) | SolarWinds (Pingdom) | monitoring | ip-list | Pingdom |
| [Pinterestbot](robots/pinterestbot.md) | Pinterest | social-preview | reverse-dns | Pinterest |
| [Qwantbot](robots/qwantbot.md) | Qwant | search-engine | both | Qwant |
| [RavenCrawler](robots/ravencrawler.md) | Raven Tools (TapClicks, Inc.) | seo | none | - |
| [Reflectionbot](robots/reflectionbot.md) | Reflection AI | ai-training | both | Reflection |
| [Riddler](robots/riddler.md) | F-Secure (riddler.io is registered to WithSecure Corporation) | research | none | Riddler |
| [RootCrawl](robots/rootcrawl.md) | RootCrawl (operated by DataChaser) | archive | web-bot-auth | RootCrawl |
| [RyteBot](robots/rytebot.md) | Semrush (formerly Ryte GmbH, acquired by Semrush in 2024) | seo | none | Semrush |
| [SeekportBot](robots/seekportbot.md) | SISTRIX | search-engine | ip-list | Seekport |
| [SemanticScholarBot](robots/semanticscholarbot.md) | Allen Institute for AI (Ai2) | research | none | - |
| [SemrushBot](robots/semrushbot.md) | Semrush | seo | reverse-dns | Semrush |
| [SemrushBot-ESI](robots/semrushbot-esi.md) | Semrush | seo | none | Semrush |
| [SemrushBot-FT](robots/semrushbot-ft.md) | Semrush | seo | none | Semrush |
| [SemrushBot-OCOB](robots/semrushbot-ocob.md) | Semrush | seo | none | Semrush |
| [SemrushBot-SWA](robots/semrushbot-swa.md) | Semrush | seo | none | Semrush |
| [SenderBot](robots/senderbot.md) | Sender Online Marketing GmbH | marketing | none | - |
| [SentryUptimeBot](robots/sentryuptimebot.md) | Sentry | monitoring | ip-list | Sentry |
| [SEOkicks](robots/seokicks.md) | Jobkicks SLU (SEOkicks) | seo | none | SEOkicks |
| [SERankingBacklinksBot](robots/serankingbacklinksbot.md) | SE Ranking | seo | both | SE Ranking |
| [SeznamBot](robots/seznambot.md) | Seznam.cz, a.s. | search-engine | both | Seznam |
| [ShapBot](robots/shapbot.md) | Parallel Web Systems | ai-search | ip-list | Parallel |
| [Shields.io](robots/shields.io.md) | Shields.io (open-source project) | other | none | Shields.io |
| [Sirportly t.co expander](robots/sirportly.md) | Krystal Hosting Ltd (Sirportly) | other | none | Sirportly |
| [SiteAuditBot](robots/siteauditbot.md) | Semrush | seo | both | Semrush |
| [Slackbot-LinkExpanding](robots/slackbot-linkexpanding.md) | Slack | social-preview | none | Slack |
| [SleepBot](robots/sleepbot.md) | Unknown | unknown | none | SleepBot |
| [SofyaBot](robots/sofyabot.md) | Sofya | ai-search | both | Sofya |
| [Sogou web spider](robots/sogou-web-spider.md) | Sogou | search-engine | none | Sogou |
| [SpiderFoot](robots/spiderfoot.md) | Intel 471 (SpiderFoot HX); the open-source version is run by its users | other | none | SpiderFoot |
| [SplitSignalBot](robots/splitsignalbot.md) | Semrush | seo | none | Semrush |
| [Stripebot](robots/stripebot.md) | Stripe | other | reverse-dns | Stripe |
| [TalarionSearchBot](robots/talarionsearchbot.md) | Talarion, Inc. | ai-search | none | - |
| [TikTokSpider](robots/tiktokspider.md) | TikTok (ByteDance), by its user agent; not confirmed by TikTok documentation | unknown | none | TikTok |
| [Twitterbot](robots/twitterbot.md) | X Corp. (formerly Twitter) | social-preview | both | Twitter |
| [um-LN](robots/um-ln.md) | Ubermetrics Technologies | marketing | none | Ubermetrics |
| [UptimeRobot](robots/uptimerobot.md) | UptimeRobot | monitoring | ip-list | Uptime Robot |
| [VelenPublicWebCrawler](robots/velenpublicwebcrawler.md) | Velen (for Hunter) | other | none | Velen |
| [VivianCrawler](robots/viviancrawler.md) | unknown | search-engine | none | - |
| [yacybot](robots/yacybot.md) | YaCy users (open-source peer-to-peer search engine project) | search-engine | none | - |
| [Yahoo! Slurp](robots/slurp.md) | Yahoo | search-engine | none | Yahoo |
| [YahooMailProxy](robots/yahoomailproxy.md) | Yahoo | other | ip-list | Yahoo |
| [YandexBot](robots/yandexbot.md) | Yandex | search-engine | reverse-dns | Yandex |
| [Yeti](robots/yeti.md) | Naver | search-engine | both | Naver |
| [YisouSpider](robots/yisouspider.md) | Shenma (by Hyperwatch's hostname rule; not confirmed by Shenma documentation) | unknown | none | Shenma |
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
