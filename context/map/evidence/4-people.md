# Evidence: people

Window 2022-01-17..2026-10-17. Human commits counted: 1060 (bots 893 and the 8 mass commits excluded; the HEAD scaffolding commit by the current user excluded as noise). Distinct human identities after merging aliases by name/e-mail (Martin Costello's two identities, Martin Tomka's two spellings, Adam Novak, a mangled-encoding name): **63** (the scan contract said ~55; same data, different alias merging). Commits are counted once per capability touched, so per-capability totals sum above 1060. Unattributed volume: `unmapped` 27 commits (2.5% of counted commits, mostly early `src/` root files).

Baseline (evidence): team-wide share of counted commits is Martin Costello 43% (453), Martin Tomka 31% (329), peter-csala 6% (68), Simon Cropp 4% (47), ZLoo 4% (43); the other ~58 identities share ~12%. Two maintainers carry ~74%, so "one person carries 40-50%" is the baseline, not a signal. Time baseline (evidence): Martin Tomka committed 2023-03..2024-05 only; Costello throughout. In the last 24 months (2024-11..) Costello has ~182 of ~210 non-bot commits; every other person has 6 or fewer. Short bursts by others are mostly mechanical sweeps (ZLoo 2024-07 and Dmitrij 2024-04..07: analyzer-warning fixes CA1062/CA1716/IDE/SA; Simon Cropp 2022-12..2023-01: nullable/whitespace/target-typed-new cleanups). These are broad-touch noise (false-signals rules 5/12), not domain expertise.

Areas: all high/medium-criticality capabilities in the inventory (core-pipeline, retry, circuit-breaker, timeout, fallback, hedging, rate-limiting, chaos, telemetry-di, legacy-v7-api, shared-foundations, platform-infra) plus docs-planning (top 5 by counted changes, low criticality). Low/legacy capabilities (bulkhead-v7, caching-v7, testing-support) are listed briefly.

## People per capability
(commits, share of that capability's commits, active period; topics from touched dirs/subjects)

| Capability (commits, distinct people) | People: commits (share), period | Topic groups |
|---|---|---|
| core-pipeline (285, 17) | Martin Tomka 194 (68%) 2023-03..2024-04; Martin Costello 58 (20%) 2023-03..2026-09; peter-csala 14 (5%) 2023-10..2025-05 | v8 pipeline/builder/registry construction (Tomka); maintenance and issue fixes (Costello); reactive/extensibility docs (peter-csala) |
| retry (159, 18) | Tomka 85 (53%) 2023-04..2023-11; Costello 32 (20%) 2022-12..2026-09; Cropp 13 (cleanup sweep); ZLoo/gintsk 6 each | v8 retry strategy + sample (Tomka); v7 retry and ongoing fixes (Costello) |
| circuit-breaker (146, 20) | Tomka 71 (49%) 2023-04..2024-01; Costello 28 (19%) 2022-12..2026-04; Cropp 15 (sweep); ZLoo 7, Dmitrij 4 (warning fixes) | controller, health metrics, state machine (Tomka) |
| timeout (121, 15) | Tomka 53 (44%) 2023-03..2024-02; Costello 31 (26%) 2022-01..2026-09 | v8 and v7 timeout |
| fallback (99, 11) | Tomka 52 (53%) 2023-04..2023-08; Costello 16 (16%) 2022-12..2025-09 | v8 fallback |
| hedging (98, 9) | Tomka 73 (74%) 2023-04..2023-10; Costello 16 (16%) 2023-09..2026-09; peter-csala 3 | v8-only; hedging controller; one Copilot-authored fix 2026-03 |
| rate-limiting (126, 13) | Tomka 56 (44%) 2023-04..2023-09; Costello 34 (27%) 2022-01..2026-09 | v8 RateLimiting package + v7 RateLimit policy |
| chaos (49, 8) | Costello 17 (35%) 2023-10..2025-12; Tomka 13 (27%) 2023-09..2024-04; peter-csala 10 (20%) 2024-01..2025-02; Geovanny Alzate Sandoval 5 (10%) 2023-09..2024-03 | Simmy outcome/fault/latency/behavior strategies; chaos docs (peter-csala) |
| telemetry-di (167, 12) | Tomka 111 (66%) 2023-03..2024-05; Costello 43 (26%) 2023-06..2026-09; peter-csala 4 | telemetry events/metrics, AddResiliencePipeline, enrichment |
| legacy-v7-api (179, 17) | Costello 65 (36%) 2022-01..2026-09; Tomka 26 (15%) 2023-03..2023-09; Cropp 24 (13%); ZLoo 23 (13%) 2024-07 (18 fix-subject commits, warning sweep); Baranyai Mate 9 2024-01..03 | wrap/NoOp/registry, bridge to v8; analyzer-warning sweeps |
| shared-foundations (167, 17) | Tomka 92 (55%) 2023-03..2024-01; Costello 44 (26%) 2022-01..2026-09 | Utils/ObjectPool, TestUtils, polyfills |
| platform-infra (442, 19) | Costello 295 (67%) 2022-01..2026-10; Tomka 106 (24%) 2023-03..2024-01 (benchmarks, mutation tests); Cropp 16 | CI workflows, build/Cake, packaging, benchmarks |
| docs-planning (255, 27) | Costello 101 (40%); Tomka 59 (23%); peter-csala 56 (22%) 2023-09..2025-09 | docs site, strategy pages, README/CHANGELOG |
| bulkhead-v7 (54), caching-v7 (81), testing-support (39) | bulkhead/caching: Costello 19/21, Cropp 14/24, ZLoo 5/16 (CA warning fixes), many one-off authors; testing-support: Tomka 24 (62%) 2023-07..09, Costello 15 (38%) 2023-09..2026-09 | testing-support has only two people ever |

Last 24 months (counted human commits since 2024-11): Costello holds 70-100% everywhere (platform-infra 121/128; legacy-v7-api 34/34; caching-v7 15/15; testing-support 11/11; core-pipeline 25/30; telemetry-di 20/24; circuit-breaker 13/15; hedging 9/13). Others appear as one-off contributors with 1-2 commits per capability (e.g. Pent Ploompuu, Daniel Rosenberg; peter-csala 2-4 on docs/core).

## Concentration
Baseline: two maintainers (Costello 43%, Tomka 31%) are the project's normal shape (evidence).
- Tomka is far above his 31% baseline in hedging 74%, core-pipeline 68%, telemetry-di 66%, testing-support 62%, shared-foundations 55%, retry 53%, fallback 53%, circuit-breaker 49% (evidence). His commits end 2024-05 (evidence), so this reads as "original v8 author, no longer committing", not live concentration.
- Costello is well above his 43% baseline in platform-infra over the full window (67%), and holds ~70-100% of every capability in the last 24 months (evidence). Live concentration = one active maintainer; formal ownership unknown.
- Capabilities touched by only one person ever: none (each has 2 or more people; testing-support, exactly 2, is the thinnest).
- Mechanical, not expertise (false-signals 5/12): ZLoo, Dmitrij, Simon Cropp, gintsk and Baranyai Mate counts in legacy-v7-api, caching-v7, bulkhead-v7, circuit-breaker are analyzer-warning or style sweeps. The infra fix-subject count (36 of 295 for the top author) is CI iteration, not instability.

## Agent co-authorship
Evidence: negligible. 1 commit authored by "Copilot" (hedging controller fix, 2026-03) and 1 `Co-authored-by: copilot-swe-agent[bot]` trailer; no Claude/Codex/Cursor trailers in the window. Share: hedging ~1% (1/98); every other capability 0%. Human Co-authored-by trailers (Costello 45, Tomka 3, peter.csala 2, others 1) are human pair attributions. Bot trailers (dependabot 641, polly-updater-bot 69, github-actions 6) belong to the excluded bot commits.

## Implications
- v8 strategy internals (hedging, core pipeline, telemetry/DI, circuit-breaker state machine, retry, fallback, shared utils): design author is Martin Tomka (2023-2024); the current maintainer Martin Costello has touched all of them since. Inference: ask Costello first; read Tomka's 2023-04..2024-04 PRs for design rationale.
- Docs semantics and chaos: peter-csala (strategy docs, Simmy docs/tests) plus Costello.
- Platform/CI/release/signing: almost only Costello (inference: bus-factor risk for releases, relevant to the high criticality of platform-infra).
- v7 legacy (policy, bulkhead, cache): Costello is the only recent committer; other authors did sweeps. Original v7 designers are mostly before the window (one appears only as a co-author trailer).
- Big 2022-12..2023-01 and 2024-07 bursts will dominate blame; check PR titles and `.git-blame-ignore-revs` before concluding anyone knows a line.

## Unknowns
- Who is on the team now and who reviews/merges: git authorship does not show reviewers or merge rights (unknown; forge discussion evidence may fill this).
- Formal ownership (CODEOWNERS) was not examined in this pass (unknown).
- Whether Tomka and peter-csala remain involved off-repo (unknown); Tomka's last commit 2024-05, peter-csala's 2025-09.
- Undetected duplicate identities could inflate the 63 count (low impact on top authors).
- Pre-2022 history (v7 era) is outside the window.

## Commands run
- `py -3 -I context/map/.work/people.py` (python3 is not available in this shell; reads `.work/git-log.txt` and `.work/capabilities.tsv`, output saved to `.work/people-out.txt`): per-capability and per-author counts, periods, fix-subject counts, last-24-month split, agent flags.
- `git log --since=2022-01-01 --no-merges --format=%B | grep -i co-authored-by | sort | uniq -c`, and `git log ... --grep=co-authored-by` (735 commits): trailer counts.
- Inline `py -3 -I` over `git log --no-merges --format=...` for author periods, subject samples and last-12/24-month activity.
