# Agents

How to add or update robot files and the identities index. Follow it step by step, so that every
run applies the same rules and the diff shows only what changed.

## What goes where

- `robots/<name>.md`: one file per robot, named after its user agent token in lowercase
  (`robots/ahrefsbot.md`). Use [`TEMPLATE.md`](TEMPLATE.md): same front matter fields, same
  sections, same order. Variants that share a `robots.txt` token and a documentation page go in one
  file (`Baiduspider`, `Baiduspider-image`, `Baiduspider-render`). Robots with their own token get
  their own file (`Amzn-SearchBot` next to `Amazonbot`).
- [`identities.md`](identities.md): every identity Hyperwatch sets, how it is verified, and the
  robot files it covers. See [Identities index](#identities-index).
- `README.md`: the robots table, one row per file, sorted by name (case-insensitive). Update it
  whenever a file is added or its front matter changes.

A robot is anything that fetches pages on its own or on someone's behalf: crawlers, AI fetchers,
link previews, feed readers, monitoring, image proxies. Webhook senders (payment notifications)
are not robots: list them in `identities.md` only.

## Sources

1. The operator's own pages first: its bot documentation, published IP lists, `robots.txt` help.
   Fetch them; don't rely on memory. Record each URL with the date checked in "Sources".
2. Other sources (Wikipedia, articles, other bot databases) only for what the operator doesn't say,
   named as such in the text ("According to …").
3. What isn't documented says "Not documented". Never fill a gap with a guess, a typical value or
   another robot's behavior.
4. For an IP list, give its URL, format, number of prefixes and the date the list says it was
   generated, on the day you checked it. Don't copy the prefixes unless there are three or fewer.
5. For Web Bot Auth (signed requests, RFC 9421), give the `Signature-Agent` value the robot sends
   (`"https://crawler.exa.ai"`), its key directory
   (`<agent>/.well-known/http-message-signatures-directory`), the number of keys, whether the
   signatures' `keyid` is the key's JWK thumbprint or the directory's `kid`, and the date you
   fetched the directory. Never copy the keys.
6. A robot whose operator can't be found: `operator: Unknown`, `category: unknown`, and say what
   was searched.

## Hyperwatch section

Read Hyperwatch's source at the version named in `identities.md`, not memory:

- the agent family: parse every user agent of the file with the `@hyperwatch/useragent` version
  Hyperwatch depends on at that version (its `package.json`), not whatever is installed elsewhere
  (`node -e "console.log(require('@hyperwatch/useragent').parse(process.argv[1]).family)" '<ua>'`,
  run from the Hyperwatch checkout);
- the identity rule, in the order `augment()` applies it in `src/modules/identity.js`:
  1. "signed only": the `signedOnly` map, before the families: a verified signature of one of its
     agents gives the identity whatever the user agent;
  2. the `case` for that family;
  3. after the `switch`, for any user agent: the "Hostname only" fallback, Google's fetcher pools
     (`googleFetcher`: special-case crawlers, user-triggered agents, user-triggered fetchers),
     then the "Signature" fallback;
- the lists the rule uses in `src/data/`: `*-ips.json` (published lists) and
  `webbotauth-agents.json` (the signers whose key directories Hyperwatch fetches; their keys are
  in `webbotauth-keys.json`).

Say exactly what the rule checks, in the terms below, and where it falls short of the operator's
documentation (a missing range, a hostname suffix not documented, a list not used). Read the code
carefully: `hostname` is the unconfirmed reverse DNS name, `verifiedHostname` the forward-confirmed
one. Don't call a check forward-confirmed unless it uses `verifiedHostname`. Write hostnames as the code has them:
the pattern given to `hostnameMatches`, or the suffix given to `endsWith`.

| Term | Rule |
|---|---|
| published list | the address is in a list from `src/data/`, fetched from the operator |
| inline range | the address is in a range written in `identity.js` |
| forward-confirmed hostname | `verifiedHostname` matches a pattern (`crawl-*.googlebot.com`: `*` stands for part of one label) or ends with a suffix (`.ahrefs.com`) |
| unconfirmed hostname | `hostname` matches a pattern or ends with a suffix: whoever controls the address's reverse DNS can set it |
| cloud hostname | `hostname` ends with a cloud provider's suffix (`*.compute-1.amazonaws.com`, `*.googleusercontent.com`, `*.your-server.de`): any customer of that provider passes |
| header | a request header's value, not checked cryptographically |
| signature | the request's header fingerprint (`signature.id`) |
| verified signature | the `webbotauth` module verified the request's Web Bot Auth signature (RFC 9421) with a key of the agent's directory (`signedBy(log, agent)` in a family rule, or the `signedOnly` map); only when the module is active. Keys are found by JWK thumbprint or by the directory's `kid`, and the profile is draft-ietf-webbotauth-httpsig-protocol-01's (`created`, `expires`, `keyid`, `tag` required; any nonce; a bare-URL `Signature-Agent` accepted) |

## Front matter: verification

`verification.method` says how the operator lets anyone verify its robot:

| Value | Meaning |
|---|---|
| `ip-list` | a published list of addresses (`ip_list`: its URL) |
| `reverse-dns` | reverse DNS names, confirmed by a forward lookup (`hostnames`: the documented patterns or suffixes) |
| `both` | a published list and reverse DNS |
| `web-bot-auth` | signed requests (RFC 9421) and a key directory, without a published list or hostnames |
| `none` | nothing published |

A robot that signs its requests and also publishes a list or hostnames keeps `ip-list`,
`reverse-dns` or `both`: say in "IP ranges and verification" that it also signs (rule 5 of
[Sources](#sources)).

## Observed parts

"Observed HTTP headers" and the "### Observed" part of "IP ranges and verification" come from
traffic of a site running Hyperwatch. Without access to such data, write
"No requests from this robot were captured with their headers yet." and leave out "### Observed".
Never invent observations, and never take them from another source.

With data, the rules in the README apply: no site names, no request counts (only "fewer than 10",
"dozens of", "hundreds of", "thousands of"), no client addresses, only the robot's own requests
(verified ones when Hyperwatch has an identity), no headers set by the site's own code or by the CDN
(`accept-encoding`, `if-none-match`, `if-modified-since`). Networks only when no ranges are
published; hostnames only when different from the documented ones.

## Last seen

The "Last seen" column of `identities.md` comes from the logs of a site running Hyperwatch: the
month (`2026-11`) of the latest request verified as the identity, or "-" when none was seen since
its logs start. Look identities up by the name that site's Hyperwatch version gives them, and
filter by nothing else. Update the column at each refresh of the index, and only move a month
forward or to "-" from what the logs show: no guess, no reason for an absence.

## Identities index

`identities.md` lists every identity set in `src/modules/identity.js`, sorted by name:

| Column | Content |
|---|---|
| Identity | the exact string set |
| Agent families | the `case` values leading to it, and "signed only", "hostname only" or "signature" when one of those leads to it for any user agent (say which agent, hostname or fingerprint) |
| Check | the terms above, joined with "or" as in the code |
| Robot files | links to the files it covers, or "-" |

When the identity rules change, update the version line at the top of `identities.md`, re-check
every row and every robot file's "Hyperwatch" section and `hyperwatch` front matter.

## Public repository

This repository is public. Never name the sites where traffic was observed, never give request
counts or client addresses, never include credentials or tokens.

## Commits

One commit per logical change, with a plain message saying what changed ("Add AhrefsBot, DotBot
and DataForSeoBot", "Update Twitterbot ranges"). Update `last_checked` in every file you checked.
