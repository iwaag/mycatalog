_Review by summoner-agent, 2026-11-17, catalog 89f51a8af07ade0e3ed18bef2fd77d890c2357dd._

The braindump `agdev` is three lines (unchanged since b7f0faf). This refreshes the earlier review (387823b); the main change is that the braindump now grounds the project `summoner` in plan agdev-a, so the review reads that project's records. Nothing cites the braindump yet.

| What it asks | What exists now | Where |
|---|---|---|
| agdev is an auxiliary tool for workflow-oriented development through the cooperation of several agent projects | Real. `agdev` (WFE, executor, Observer, installation) runs workflows as runs; the plan agdev-a holds many cooperating adopted projects, and `wfe summon status` shows roles filled by warden, ponderer and aghangout. `agdev` has completed 13 `freework` runs. | project `agdev` README; `wfe projects runs agdev`; `wfe summon status` |
| At start-up, summoner collects development-support projects in line with the development style | Real as a mechanism, and used here. `summoner` is in the plan (adopted) and has completed runs of its support workflows: advise (3), ask (6), ground (4), index (5) (and review runs). The README describes `agdevctl bootstrap-projects` bringing the summoner first, then `summoner/propose` or `wfe summon style <user>`. | project `summoner` runs; agdev README "To start a new installation" |
| A summoner-like agent must be there first, or collecting is done by hand ("面倒") | Consistent with the core naming the summoner as the one project it brings first. | agdev README |
| agdev can place a mirror of itself among the subordinate projects | Partly. `agdev` is a managed project (`developer/agdev`) and the README/docs describe a child installation managed by a parent. Whether that is the "mirror under subordinate projects" meant is not established. `agdev` itself is "not in the plan" of agdev-a. | agdev README; docs/install.md "Managing a child installation" |

## Not real / open
- The mirror sentence is ambiguous; no record shows a mirror of agdev placed under a project as a sub-project.
- `agdev` is registered but not in the plan, so the braindump's subject has no plan entry; the braindump grounds only `summoner`. This review writes no link.
- No open challenges name `summoner`.

## Not checked
- The start-up from a clean host was read from the README, not from runs; whether any summoner run did that start-up.
- Contents of the `agdev` freework runs, and whether any concerns a mirror.
- Whether the `propose` workflow itself has been run (only its sibling workflows were seen in the run list excerpt read).
