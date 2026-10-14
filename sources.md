# Source Registry

Access methods, as tested on 2026-10-14 from the cloud session:

| Method | What it is | Status |
|---|---|---|
| `search` | Claude WebSearch tool (runs outside the container) | **Works.** Main discovery channel. Gives summaries and URLs, not full page text. |
| `fetch` | Claude WebFetch tool | **Broken this session.** DNS failure on every external host tried (arxiv.org, techcrunch.com, adversa.ai, helpnetsecurity.com). |
| `curl` | Direct HTTP from the container (`scripts/collect.py`) | **Allowlisted hosts only.** `www.anthropic.com` works. arxiv, openai.com, deepmind.google, GitHub API, OWASP, NVD, X and LinkedIn are blocked by the environment network policy. |
| `gh-mcp` | GitHub MCP tools | Limited to this repo's scope. Can't do general repo search. |

Status values: ✅ checked OK · ⚠️ partial (search snippets only, primary page not opened) · ❌ blocked · ⏳ not yet tried.
"Last check" is the most recent successful check.

## A. Frontier labs (primary)

| Source | URL | Category | Access | Status | Last check |
|---|---|---|---|---|---|
| Anthropic sitemap (news/research/engineering diff) | https://www.anthropic.com/sitemap.xml | lab-primary | curl | ✅ | 2026-10-14 |
| Anthropic Research | https://www.anthropic.com/research | lab-primary | curl | ✅ | 2026-10-14 |
| Anthropic Engineering | https://www.anthropic.com/engineering | lab-primary | curl | ✅ | 2026-10-14 |
| Anthropic Transparency hub / system cards | https://www.anthropic.com/transparency | lab-primary | curl | ⏳ | — |
| OpenAI News RSS | https://openai.com/news/rss.xml | lab-primary | curl (blocked) → search | ❌ / ⚠️ | 2026-10-14 (search) |
| OpenAI Safety / system cards | https://openai.com/safety | lab-primary | search | ⚠️ | 2026-10-14 |
| Google DeepMind blog RSS | https://deepmind.google/blog/rss.xml | lab-primary | curl (blocked) → search | ❌ / ⚠️ | 2026-10-14 |
| Google Security Blog | https://security.googleblog.com | lab-security | search | ⏳ | — |
| Google Threat Intelligence (GTIG) | https://cloud.google.com/blog/topics/threat-intelligence | threat-intel | search | ⚠️ (report not located) | 2026-10-14 |
| Meta AI blog | https://ai.meta.com/blog | lab-primary | search | ⏳ | — |
| Microsoft Security / MSRC blog | https://msrc.microsoft.com/blog | lab-security | search | ⏳ | — |
| xAI news | https://x.ai/news | lab-primary | search | ⏳ | — |
| UK AISI | https://www.aisi.gov.uk | gov-eval | search | ⏳ | — |
| NIST CAISI | https://www.nist.gov/caisi | gov-eval | search | ⏳ | — |
| METR | https://metr.org | eval-org | search | ⏳ | — |

## B. Vulnerabilities and advisories

| Source | URL | Category | Access | Status | Last check |
|---|---|---|---|---|---|
| CISA KEV catalog | https://www.cisa.gov/known-exploited-vulnerabilities-catalog | advisory | search | ⚠️ | 2026-10-14 |
| GitHub Security Advisories (MCP SDKs, LiteLLM, LangChain, Langflow) | https://github.com/advisories | advisory | search / gh-mcp | ⏳ | — |
| NVD | https://nvd.nist.gov | advisory | curl (blocked) | ❌ | — |
| Vulnerable MCP Project | https://vulnerablemcp.info | mcp-db | search | ⚠️ | 2026-10-14 |
| CSA AI Safety Labs research notes | https://labs.cloudsecurityalliance.org/research/ | analysis | search | ⚠️ (good aggregator, dated notes) | 2026-10-14 |
| Wiz vulnerability DB / research | https://www.wiz.io/vulnerability-database | advisory | search | ⚠️ | 2026-10-14 |
| OWASP GenAI Security Project | https://genai.owasp.org | framework | curl (blocked) → search | ❌ | — |

## C. Independent researchers and offensive blogs

| Source | URL | Category | Access | Status |
|---|---|---|---|---|
| Embrace The Red (Johann Rehberger) | https://embracethered.com/blog/ | researcher | search | ⏳ |
| Simon Willison (prompt injection tag) | https://simonwillison.net/tags/prompt-injection/ | researcher | search | ⏳ |
| Adversa AI monthly roundups (coding agents, MCP) | https://adversa.ai/blog/ | aggregator | search (fetch failed) | ⚠️ |
| Manifold Security (GitSpawn) | — locate primary | researcher | search | ⚠️ primary not found |
| Air Security (Plugin4Shell) | — locate primary | researcher | search | ⚠️ primary not found |
| Salt Labs | https://salt.security/blog | vendor-research | search | ⚠️ |
| Trail of Bits blog | https://blog.trailofbits.com | researcher | search | ⏳ |
| Invariant Labs / Snyk | https://invariantlabs.ai/blog | vendor-research | search | ⏳ |
| HiddenLayer, Lakera, Pillar, Noma, Zenity, Lasso research | vendor blogs | vendor-research | search | ⏳ |

## D. Papers

| Source | URL | Access | Status |
|---|---|---|---|
| arXiv cs.CR / cs.CL / cs.AI (API + listings) | https://export.arxiv.org/api/query | curl (blocked) and fetch (DNS fail) → search | ❌ / ⚠️ |
| Conference proceedings: USENIX Sec, IEEE S&P, CCS, NDSS, NeurIPS, ICLR, SaTML | various | search | ⏳ |

## E. Tools and repos

| Source | URL | Access | Status |
|---|---|---|---|
| promptfoo releases | https://github.com/promptfoo/promptfoo/releases | search | ⚠️ |
| garak releases | https://github.com/NVIDIA/garak/releases | search | ⚠️ |
| PyRIT | https://github.com/Azure/PyRIT | search | ⏳ |
| Tencent AI-Infra-Guard | https://github.com/tencent/AI-Infra-Guard | search | ⚠️ |
| Giskard | https://github.com/Giskard-AI/giskard | search | ⚠️ |
| MCP spec / SDK security advisories | https://github.com/modelcontextprotocol | search | ⚠️ |

## F. News and market

| Source | URL | Access | Status |
|---|---|---|---|
| The Hacker News | https://thehackernews.com | search | ⚠️ |
| Help Net Security | https://www.helpnetsecurity.com | search (fetch failed) | ⚠️ |
| TechCrunch security / AI | https://techcrunch.com | search (fetch failed) | ⚠️ |
| Dark Reading, The Register, SecurityWeek | various | search | ⚠️ |
| Crunchbase News (funding) | https://news.crunchbase.com | search | ⚠️ |

## G. Social (discovery only, never treated as proof)

| Source | Access | Status |
|---|---|---|
| X / Twitter | blocked from container, no API key | ❌ Search snippets only. **Not monitored.** |
| LinkedIn | blocked, no API | ❌ **Not monitored.** |
| Hacker News (hnrss) | curl (blocked) → search | ❌ / ⚠️ |
| Reddit r/LocalLLaMA, r/netsec | not tried | ⏳ |

## Ways to improve coverage (user action needed)

1. **Network allowlist.** Add these to the cloud environment's *Allowed domains*: `export.arxiv.org`, `arxiv.org`, `openai.com`, `deepmind.google`, `api.github.com`, `embracethered.com`, `simonwillison.net`, `hnrss.org`, `labs.cloudsecurityalliance.org`, `www.cisa.gov`, `services.nvd.nist.gov`. Then `scripts/collect.py` can pull their RSS feeds and APIs directly, which is far more reliable than search.
2. **GitHub token** (read-only, public repos) as an environment secret, to get past API rate limits for release and advisory polling.
3. **X/LinkedIn.** There is no compliant free path. Either skip them, or forward interesting posts by hand into `inbox.md`.
