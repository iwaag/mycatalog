_Review by summoner-agent, 2026-11-20, catalog bb3a0f9db0218ccd8adace91920cadbace685db1._

The braindump `agdev` changed after the review of 2026-11-17 (693f68f). The text now has a first section, "agdevの基幹ワークフロー", and a second, "iwaagのagdev運用スタイル", with four bullets. This review replaces the earlier one. Nothing has cited the braindump yet.

| What it asks | What exists now | Where |
|---|---|---|
| Wishes, tastes and thoughts are written as free-form braindumps, and workflows put them into practice, drawn and visible | Real. The catalog holds braindumps (13 here); WFE runs workflows as runs with a visible graph. This run is itself a workflow made from a catalog follow-up of a braindump change. | `wfe catalog status`; `wfe run show` |
| Workflows are split into projects by the developer's standard, and each project records and accumulates its knowledge and detail | Real. Plan agdev-a holds 19 adopted projects, each with its own runs. `agdev` has 19 `freework` runs, `summoner` has runs of ask, advise, create, catalog-publication-edit, freework, ground, index and review. | `wfe summon status`; `wfe projects runs agdev` / `summoner` |
| Braindumps are mainly typed in or ghost-written by an agent with its signature; images, video, audio may be included | Partly. Authorship by the owner and by signed agents (Git author) is seen in the catalog. Non-text media in braindumps was not seen. | `wfe catalog braindump list` |
| Project boundaries roughly match agent roles; a project may be treated as one personified agent | Consistent. Roles are filled by projects: coordination and recovery by warden, facilitation and conversation-archive by ponderer, conversation-page and dialogue-renderer by aghangout. Whether projects are treated as personified agents is a way of seeing, not checkable. | `wfe summon status` |
| At start-up, summoner collects development-support projects in line with the style, because without a summoner-like agent first the owner would have to collect them by hand | Real as a mechanism and in use. `summoner` is in plan agdev-a (adopted) and is the project this braindump grounds. It is also on another installation of the cluster (agdev-PC, summoned, main a19ed6f), as its advertisement shows; what its runs there produced was not checked. Here it has completed many runs of its workflows. | `wfe catalog why summoner`; `wfe projects runs summoner` |
| agdev may place a mirror of itself in subordinate projects (allowed) | Open. This only permits; it asks for nothing to exist. `agdev` is a registered project with 19 freework runs, but no record read shows a mirror of agdev placed under another project. | `wfe projects runs agdev` |

## Not real / open
- No record shows an agdev mirror under a subordinate project (a permission, so not a gap by itself).
- Non-text braindump media (images, video, audio) was not seen in this catalog.
- No open challenge names `summoner`.

## Not checked
- Contents of the `agdev` freework runs, and whether any concerns a mirror.
- Whether `propose` has been run on this installation (no `propose` run appears in the summoner run list read).
- What summoner's runs on agdev-PC produced.
- Operating guidance and node templates: none recorded or proposed (see run outcome); this review is not about them.

A review is someone's reading of how far a braindump has become real, at its date; check it against the present state before relying on it.
