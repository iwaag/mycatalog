_Review by summoner-agent, 2026-11-21, catalog d3b72a20a02f0408f033b5d095de556b606d70fb._

The braindump `agdev-2` ("agdevのフロントエンドについて", tags public, todo, style) changed after the review of 2026-11-20 (fbdbeae): the visualisation is now named "catalog map" instead of "catalog view". The asks are otherwise the same. This review replaces the earlier one. Nothing has cited it yet, and it grounds no project in plan agdev-a.

| What it asks | What exists now | Where |
|---|---|---|
| "catalog内のbraindumpとそれに関連するカスタムノードとプロジェクトのリストの関係図がcatalog mapという名前のビューで可視化されて欲しい" | Not found. The data such a map would draw exists: braindump cards list grounded projects and node templates (with "grounded:" marks). No view named "catalog map" was seen, and no project or run in this plan names it. The agdev UI is core, not read from here. | `wfe catalog braindump show`, `wfe catalog nodes show agdev-2` |
| "それぞれの要素がprivateなのかpublicなのか、共通のアイコンで一目でわかるようにしてほしい" | Partly. Disclosure exists as data (tags public/private, "[published]" marks in `wfe catalog status`). A common icon across braindumps, node templates and projects was not seen. | `wfe catalog status` |
| Projects shown in four categories: development-support agents, asset-production technique experiments, trend-technology experiments, real production projects | Not found as a classification. The catalog holds no record of such categories. Candidate members exist (warden, ponderer, summoner as support agents; agsfx, lowerpoly, gimmickimg grounded by `asset_projects`), but nobody has classified them. | `wfe summon status`, `wfe catalog status` |
| "プロジェクトのカテゴリ分けはエージェントが行い、その分類判断を何らかの形でcatalog内に残して欲しい" | Not found. No file in the catalog records an agent's categorisation. | catalog at d3b72a2 |

## Not real / open
- The "catalog map" view, the common public/private icon, the four-way project classification and the stored classification decisions were not seen.
- No project in plan agdev-a is grounded on this braindump; the UI work may belong to agdev itself. The `ground` workflow may suggest a link; this review writes none.
- No open challenge was looked up by name for this braindump.

## Not checked
- The agdev UI source (the core), so a view with another name or the new name may exist.
- Contents of the registered `agdev` project's runs.

## Operating guidance and node templates
Operating guidance: none. It wishes for a view and a classification; it states no rule for a recurring decision. Node templates: none. Custom nodes appear only as items drawn in the view; no expectation about a workflow step is stated.
