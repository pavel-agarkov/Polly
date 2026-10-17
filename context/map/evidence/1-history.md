# Evidence: history

Window 2022-01-17..2026-10-17 (HEAD e48c1a57), buckets = quarter (quarters with zero counted commits are absent: 2022Q2, 2022Q3). Commits in window 1962 (merges excluded); excluded 893 bots + 8 mass (kept out of all counts, see `.work/excluded-commits.txt`); counted 1061, of which 1059 touch at least one non-noise file (2 touch only noise). Non-noise file changes: 9,773 (matches the scan contract). Mapping = `capabilities.tsv` via the `coverage.py` reference logic (globs, longest segment prefix, old paths folded). Fix signal = contract regex `fix|bug|regression|hotfix|crash|leak|race|NRE` (word-ish, case-insensitive); revert = subject starts with `Revert`/`Rollback`. Label key: [E] evidence, [I] inference, [U] unknown.

## Activity per capability
[E] Commits count once per capability touched (cross-cutting commits counted in each), so commit columns do not sum to 1059.

| capability | file changes | share | commits | agent-authored commits |
|---|---|---|---|---|
| core-pipeline | 1325 | 13.6% | 285 | 0 |
| platform-infra | 1154 | 11.8% | 443 | 0 |
| circuit-breaker | 833 | 8.5% | 146 | 0 |
| legacy-v7-api | 824 | 8.4% | 179 | 0 |
| docs-planning | 755 | 7.7% | 256 | 0 |
| telemetry-di | 725 | 7.4% | 167 | 0 |
| retry | 669 | 6.8% | 159 | 0 |
| shared-foundations | 654 | 6.7% | 167 | 0 |
| hedging | 531 | 5.4% | 98 | 1 |
| chaos | 469 | 4.8% | 49 | 0 |
| rate-limiting | 428 | 4.4% | 126 | 0 |
| caching-v7 | 402 | 4.1% | 81 | 0 |
| fallback | 357 | 3.7% | 99 | 0 |
| timeout | 354 | 3.6% | 121 | 0 |
| bulkhead-v7 | 190 | 1.9% | 54 | 0 |
| testing-support | 68 | 0.7% | 39 | 0 |
| unmapped | 35 | 0.4% | 27 | 0 |

- [E] Unmapped share 0.4% (35 changes). Catch-all buckets (platform-infra, docs-planning, shared-foundations) = 26.2%, product capabilities = 73.4%.
- [E] Agent-authored: 1 commit in the window (author "Copilot", 51c138e7, "Fix non-deterministic branch coverage for HedgingExecutionContext (#2997)"); checked author name and Co-authored-by trailer for claude/copilot/codex/cursor/devin. 0.1% of counted commits; agents are not a factor in this history. The HEAD commit (10x toolkit scaffolding) touches only noise paths.
- [E] Dominant activity is the v8 API: core-pipeline + the five v8 strategies + telemetry-di + hedging + chaos + rate-limiting. v7 capabilities (legacy-v7-api, caching-v7, bulkhead-v7) together = 1,416 changes (14.5%).

## Top files in top capabilities
[E] (changes per file; paths as in history, see freshness for deleted/moved)
- core-pipeline: `src/Polly.Core/PublicAPI.Unshipped.txt` 63 (API bookkeeping, mechanical), `Polly.Core.csproj` 28, `ResilienceContext.cs` 23, `src/Polly.Core/README.md` 21, `ResilienceStrategy.cs` 19 (renamed to ResiliencePipeline in 2023), `Registry/ResilienceStrategyRegistry.cs` 18.
- platform-infra: `.github/workflows/build.yml` 88, `build.cake` 62, `Directory.Packages.props` 48, `eng/Library.targets` 27, `.config/dotnet-tools.json` 25, `gh-pages.yml` 21.
- circuit-breaker: `Controller/CircuitStateController.cs` 32 (+ its tests 27), `CircuitBreakerResilienceStrategy.cs` 22 (+ tests 23), `...BuilderExtensions.cs` 18, `CircuitBreakerManualControl.cs` 17.
- legacy-v7-api: `src/Polly/Polly.csproj` 67, `test/Polly.Specs/Polly.Specs.csproj` 32, `Utilities/TimedLock.cs` 25, `Registry/PolicyRegistry.cs` 17, `AsyncPolicy.ExecuteOverloads.cs` 17.
- docs-planning: `README.md` 66, `docs/strategies/retry.md` 29, `CHANGELOG.md` 28, `docs/strategies/circuit-breaker.md` 27, `fallback.md` 21, `timeout.md` 21.
- telemetry-di: `PollyServiceCollectionExtensions.cs` 32 (+ tests 24), `TelemetryResilienceStrategy.cs` 25, `ResilienceTelemetryDiagnosticSource.cs` 22 (+ tests 21), `TelemetryListenerImpl` tests 19.
- [I] Within circuit-breaker the state machine (`CircuitStateController`) is the single hottest file and the one with the most heavy test churn; in telemetry-di the DI registration extension is the integration point people touch.

## Trend
Counted commits per quarter (cross-cutting counted in each capability). Columns: 2022Q1-2023Q1 (pre-v8) / v8 build 2023Q2-Q4 / 2024 / 2025 / last four quarters 2025Q4-2026Q3.

| capability | pre-v8 | 2023Q2-Q4 | 2024 | 2025 | last 4q | label |
|---|---|---|---|---|---|---|
| core-pipeline | 20 | 204 | 32 | 23 | 10 | fading (spike) |
| platform-infra | 72 | 199 | 49 | 85 | 45 | constant (spike in 2023) |
| circuit-breaker | 19 | 84 | 29 | 11 | 3 | fading |
| legacy-v7-api | 48 | 32 | 66 | 29 | 6 | seasonal (2024 campaign), now fading |
| docs-planning | 14 | 149 | 53 | 28 | 12 | fading (spike) |
| telemetry-di | 2 | 124 | 18 | 15 | 9 | fading |
| retry | 16 | 98 | 27 | 17 | 4 | fading |
| shared-foundations | 23 | 101 | 17 | 19 | 8 | fading |
| hedging | 0 | 80 | 6 | 8 | 4 | fading (born 2023Q2) |
| chaos | 0 | 7 | 28 | 13 | 2 | seasonal (2024Q1 spike 21) |
| rate-limiting | 15 | 69 | 26 | 14 | 3 | fading |
| caching-v7 | 29 | 4 | 34 | 12 | 1 | seasonal (2023Q1, 2024Q1/Q3) |
| fallback | 14 | 54 | 20 | 11 | 0 | fading |
| timeout | 16 | 62 | 26 | 14 | 4 | fading |
| bulkhead-v7 | 18 | 2 | 19 | 15 | 1 | seasonal |
| testing-support | 0 | 27 | 2 | 8 | 3 | fading (one-off 2023Q3 spike 25) |

- [E] No capability is rising. Whole repo peaked in 2023Q2-Q3 (v8 alpha 2023-06, built within the window); since 2024 every v8 capability is in single-digit commits per quarter, and the last four quarters are the quietest in the window for the product capabilities.
- [E] Campaigns visible in commit subjects: v8 build-out 2023Q2-Q4 (e.g. "Alpha fixes and improvements (#1319)" 2023-06-19, "Rename ResilienceStrategy to ResiliencePipeline (#1483)" 2023-08); Simmy/chaos API review 2024-01-21..27 (Parts 1-4, "Prefer Chaos over Monkey") explains chaos 2024Q1; analyzer-warning cleanup 2024-02, 2024-07 (SonarAnalyzer/CA/IDE rule-by-rule PRs) explains the v7 spikes in caching-v7/bulkhead-v7/legacy-v7-api 2024Q1/Q3; 2025Q1 spike in v7 areas (Jan 2025 "Fix IDE0055 warnings", "Fix CA1031", flaky tests) is the same analyzer pattern.
- [E] platform-infra is the only capability with sustained activity in the last four quarters (45 commits), mostly dependency/CI/tooling work (bots excluded; remaining are human CI/tooling commits).
- [I] The codebase has moved into maintenance mode; hot-area signals for v8 strategies are historical rather than current.

## Fix pressure
Heuristic: contract fix regex on subject, per-commit signal counted for every capability touched. "Raw" is the contract number; "behavioural" removes subjects that are rule-code/warning/typo/CI/docs/tooling fixes (regex of `CA\d+|S\d{3,4}|SA\d+|IDE\d+|warning|typo|lint|style|link|badge|docs|permissions|CI|coverage|version|build|benchmarks|stryker|validation|sample|flaky|unstable|...`, applied by me; subjects of every capability were read to check it, a coarse filter - [I]).

| capability | commits | raw fix | raw % | cross-cut (>3 caps) in raw | behavioural fix | reverts (incl. spillover) |
|---|---|---|---|---|---|---|
| legacy-v7-api | 179 | 62 | 35% | 19 | 4 | 4 |
| caching-v7 | 81 | 31 | 38% | 12 | 5 | 4 |
| bulkhead-v7 | 54 | 17 | 31% | 10 | 2 | 4 |
| circuit-breaker | 146 | 26 | 18% | 13 | 7 | 4 |
| timeout | 121 | 22 | 18% | 12 | 1 | 5 |
| rate-limiting | 126 | 22 | 17% | 12 | 2 | 4 |
| retry | 159 | 26 | 16% | 13 | 7 | 3 |
| shared-foundations | 167 | 26 | 16% | 11 | 13 | 4 |
| docs-planning | 256 | 39 | 15% | 2 | 9 | 0 |
| fallback | 99 | 15 | 15% | 13 | 1 | 3 |
| hedging | 98 | 14 | 14% | 3 | 9 | 0 |
| platform-infra | 443 | 46 | 10% | 8 | 15 | 3 |
| telemetry-di | 167 | 15 | 9% | 5 | 9 | 0 |
| core-pipeline | 285 | 24 | 8% | 8 | 13 | 0 |
| chaos | 49 | 4 | 8% | 2 | 3 | 0 |
| testing-support | 39 | 1 | 3% | 0 | 0 | 0 |

- [E] Reverts: 5 commits in total (after excluding the file-scoped-namespaces revert 63b151eb). 4 are formatting reverts from 2022-12-13..16 ("Revert 'redundant type specs'/'redundant whitespace'/'expression body members'/'use var'"), each touching 8-10 capabilities; they explain essentially all revert counts above (rule 12 spillover). 1 is "Revert test change" (8dc6e8c6, 2023-06-27, timeout tests only). Product reverts: 0 of significance. [E]
- [E] The 35-38% raw fix share of the v7 capabilities is mechanical: of the 62 legacy-v7-api fix commits only 4 are not analyzer-warning/flaky-test/CI wording; caching-v7 non-cross fixes are 14 of 20 "Fix CA1062 warning(s)". Real v7 bug fixes in the window: "Fix overflow in BulkheadSemaphoreFactory (#2638)" 2025-06, "Fixed an incorrect exception argument (#915)" 2022-02, plus null-handling test fixes.
- [E] Platform-infra fix subjects read: "Fix permissions", "Fix package signing (#2631)", "Fix GitVersion...", "Fix broken CI" - iteration on CI/release, rule 5 -> mechanical.
- [E] Genuine defect fixes (read from subjects), by capability: circuit-breaker "Fix CircuitBreaker handling of Half-Open (#1991)" 2024-02, "Fix stack trace growing for opened circuit breaker (#1878)" 2024-01, "Fix `ScheduledTaskExecutor` deadlock when `TrySetResult` runs continuations inline" 2026-03 (the only recent concurrency fix); retry "Fix retry delay going negative for large retries (#2164)" 2024-06, "Fix retry overflow with max delay (#1868)" 2023-12, "Fix for retry cancellation (#2456)" 2025-02; hedging "Fix hedging being cancelled too early (#1340)", "Fix OnHedging not being called (#1320)", "Fix the behavior of OnHedging event (#1625)", "Fix #2288 (#2313)" 2024-09, race-condition test fixes, Copilot's coverage-determinism fix 2025; chaos "[Bug] Fix chaos outcome exception handling (#2101)" 2024-05; telemetry-di "Fix Name and InstanceName not being set for reloadable pipelines (#1555)", "Fix logging of execution attempt (#1341)".
- [I] timeout, fallback, rate-limiting have almost no behavioural fixes of their own (1, 1, 2); their raw numbers are spillover from the big 2023-06-19 "Alpha fixes and improvements (#1319)" commit (touches 11 capabilities) and the Dec-2022 reverts. Ranking them as fix-prone would be wrong.
- [I] Shape of real fix pressure: the concurrency/arithmetic-heavy v8 areas (circuit-breaker, retry delays, hedging) hold the real bug fixes, all in 2023-2024 with one deadlock fix in 2026. Absolute numbers are small (1-13).

## Co-change between capabilities
Rule: capability set per commit (unmapped excluded); commits touching more than half of the 16 capabilities (>8) are dropped: 42 commits dropped. Confidence = shared / commits of the less active side. Top pairs by support (full list of 30 in `.work/history-out.txt`):

| pair | support | confidence | note |
|---|---|---|---|
| core-pipeline / telemetry-di | 87 | 0.52 | v8 core plus its telemetry hooks |
| core-pipeline / shared-foundations | 81 | 0.49 | utils/pools used by core |
| core-pipeline / platform-infra | 79 | 0.28 | csproj, PublicAPI, build |
| core-pipeline / retry | 67 | 0.42 | |
| docs-planning / platform-infra | 57 | 0.22 | docs build tooling |
| caching-v7 / legacy-v7-api | 42 | 0.52 | both are `src/Polly` (v7) |
| core-pipeline / hedging | 46 | 0.47 | |
| circuit-breaker / core-pipeline | 46 | 0.32 | |
| circuit-breaker / retry | 46 | 0.32 | |
| fallback / retry | 43 | 0.43 | |
| circuit-breaker / fallback | 40 | 0.40 | |
| retry / timeout | 44 | 0.36 | |

- [E] Strongest non-infrastructure coupling: core-pipeline with telemetry-di, hedging and retry (confidence 0.42-0.52). Strategy-to-strategy pairs (retry/timeout/fallback/circuit-breaker/rate-limiting) co-change at 0.26-0.43, which fits a shared options/builder/telemetry pattern touched in sweeps [I].
- [I] Much of the strategy-to-strategy co-change is sweep-style work (analyzer fixes, API review, renames) rather than one strategy needing another; it does not show a semantic dependency.
- Dropped >half-of-capabilities commits: 42 (e.g. the mass renames/sweeps), reported as events not as coupling.

## Hub files and freshness
Hubs = files whose commits also touch the most distinct other capabilities (partner counted if seen in at least 2 commits). Top: `src/Polly.Core/PublicAPI.Unshipped.txt` 13 partners (52 commits), `src/Polly/Polly.csproj` 12 (64), `test/Polly.Specs/Polly.Specs.csproj` 12 (24), `test/Polly.Core.Tests/Retry/RetryResilienceStrategyTests.cs` 12 (23), `src/Polly.Extensions/Telemetry/TelemetryResilienceStrategy.cs` 11 (20), `Directory.Packages.props` 10 (42), `src/Polly.Core/Retry/RetryResilienceStrategy.cs` 10, `PollyServiceCollectionExtensions.cs` 10, `ResilienceContext.cs` 10, `Polly.Core.csproj` 9.
- What they are: PublicAPI.Unshipped.txt = API-surface bookkeeping, a lockstep file guarded by the public-API analyzer (rule 3, mechanical); `*.csproj` and `Directory.Packages.props` = shared project/package config (mechanical, rule 4); `ResilienceContext.cs`, `RetryResilienceStrategy.cs`, `PollyServiceCollectionExtensions.cs` = real shared-API hubs, but their partner counts come largely from the same API-review/rename sweeps [I].
- [E] No generated clients, schemas or translation catalogs exist as hubs here.
- Freshness (`git cat-file -e HEAD:<path>`, 47 files named in this report): 38 exist, 9 do not. Gone: `src/Polly.Core/PublicAPI.Unshipped.txt` (moved to a new baseline location in "Move Public API baselines (#3016)" 2026-04-03), `src/Polly.Extensions/Telemetry/TelemetryResilienceStrategy.cs` (dropped 2023-08, #1482), `src/Polly.Extensions/Telemetry/ResilienceTelemetryDiagnosticSource.cs`, `src/Polly.Core/Retry/RetryResilienceStrategyBuilderExtensions.cs` and `CircuitBreakerResilienceStrategyBuilderExtensions.cs` (builder rename, #1448), `src/Polly.Core/Registry/ResilienceStrategyRegistry.cs` (renamed to pipeline registry, #1483), `build.cake` (-> cake.cs/build.ps1), `src/Polly.Specs/Polly.Specs.csproj` (moved to test/, reorg #1289), `test/Polly.Extensions.Tests/Telemetry/ResilienceTelemetryDiagnosticSourceTests.cs`. These describe the past; capabilities already fold them (rule 11). Notably the "TelemetryResilienceStrategy" hub (11 partners) no longer exists.

## Mechanical signals
- Raw fix share of v7 capabilities (31-38%): analyzer-warning sweeps (rule 5, 7-like); behavioural fixes 2-5.
- Revert counts (3-5 per capability): one Dec-2022 formatting-revert cluster spilling over 8-10 capabilities (rule 12); 0 product reverts.
- timeout/fallback/rate-limiting raw fix and cross-cutting counts: spillover from "Alpha fixes and improvements (#1319)" (rule 12).
- platform-infra fix ratio 10% and high commit count: CI/release iteration (rule 5); its co-change with core-pipeline/docs is the build and API-baseline workflow (rules 3, 4).
- PublicAPI.Unshipped.txt as top file of core-pipeline and top hub: API-bookkeeping lockstep (rule 3), a build analyzer fails loudly on drift [I, check not performed here].
- docs-planning is prose/samples churn (rule 8): 256 commits but not a hot area.
- 2023Q2-Q4 spike is the v8 build campaign; it is both "busy" and "planned" for the same reason (rule 4) and should be counted once.
- Agent commits: 1 (rule 7), not a signal.

## Unknowns
- [U] Pairs that should co-change but are not detectable here: v8 strategy options/public API versus docs/strategies pages (docs-planning only co-changes with core-pipeline at 0.16 confidence); v7 policy to v8 bridge behaviour; `Polly.Testing` (testing-support) versus the pipeline description it inspects (only 39 commits; no evidence either way).
- [U] External consumers of the NuGet packages (Polly, Polly.Core, Polly.Extensions, Polly.RateLimiting, Polly.Testing) live outside the repo; their coupling to API changes is unknown (rule 10).
- [U] Bug-labelled issue references were not used (no forge data in this source); fix share is subject-only and can miss fixes titled without the keywords.
- [U] Whether PublicAPI baseline drift fails the build (no check run; rule 3 assumed from convention).
- [U] File-level hub/top-file numbers use the path as it was at commit time; old `src/Polly.*Tests` paths are mapped to capabilities but not merged with their `test/...` successors file by file, so file-level counts may be split across old and new names.
- [U] Quarters 2022Q2 and 2022Q3 have no counted commits (all human commits were mass-excluded or absent); not investigated.

## Commands run
- `python -I` over `.work/git-log.txt` with `coverage.py`'s `cap()`/noise/bot/mass logic: script `.work/history.py`, outputs `.work/history-out.txt`, `history-out2.txt`, `history-fix.json`, `history-revert.json`, `history-hubs.txt`, `history-named-files.txt`
- `git cat-file -e HEAD:<path>` for each of 47 named files
- `git -c core.quotepath=off log --no-merges --follow -M --name-status` on four moved/deleted files; `git log` on `src/Polly.Core/Simmy` for 2024-01..04 and a count of "Fix .* warning" subjects in 2024-07 (39)
- `git ls-files | grep -c PublicAPI` (10)
