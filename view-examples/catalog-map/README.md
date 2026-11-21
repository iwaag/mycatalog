# Catalog Map — a view example

A portable description of one optional view over a catalog: braindumps, the custom workflow nodes
they ground and the projects they ground, drawn as one map, with one disclosure legend and the
projects grouped by categories the owner chose.

This is an example to adapt, not a part of agdev's core. The core shows braindumps, projects and
the links between them. Which categories a project falls in, what the map is called and how it looks
are an owner's style. The example gives no HTML, CSS or JavaScript: you (or your agent) write the
page, and it is yours. An installation without the map loses nothing: the core's Catalog page and
its relation diagram work the same with no view and no link.

Everything named in `example.yaml` below `fictional:`, and every id, host and commit in this file,
is invented.

## Adopting it

1. Read `example.yaml` at one revision of this catalog and note that revision (the commit).
2. In your own catalog, create `views/catalog-map/` with the two records described under
   *Your records*: your categories and decisions, and which example revision you started from.
   Rename, drop or add categories until they are yours.
3. Let an agent classify your own projects from your own braindumps. Each decision carries its
   reason and a reference to the evidence. Leave a project `unclassified` when the evidence does
   not decide it.
4. Implement the page in your installation's own source under `local-views/<view>/` (see *Where the
   page lives*). It reads the live facts from your installation (*What the page reads*) and your
   decisions from one generated file (*Your decisions in the browser*).
5. Build a release from the commit that has the page, and, if you want a button on the Catalog
   page, add the link (*The optional Catalog link*).

## What the page reads

Three reads of the installation's workflow editor service (WFE), all `GET`, all read-only, all part
of the core. The page writes nothing.

| Read | What the map takes from it | Core document |
| --- | --- | --- |
| `api/catalog` | the braindumps, the projects with the braindumps that ground them, pending link suggestions, what the owner stated about disclosure | `workflow_editor/docs/mycatalog.md` |
| `api/nodes` | the custom node templates with the braindump passages that ground each revision | `workflow_editor/docs/node-catalog.md` |
| `api/catalog/publication/facts/<catalog-project>` | what the catalog's publication contract selects and what the last publication carried | `docs/external-publication.md` (*Seeing and changing it from the Catalog page*) |

`<catalog-project>` is the name of the catalog repository: the part of `repository` in
`api/catalog` after the slash. The core fixes it to `mycatalog`.

**Resolve them relative to the page.** The service serves your page at
`<wfe>/local-views/<view>/index.html`, where `<wfe>` is whatever address the service is opened by:
its own port (`http://host.example:8098/`) or a route of the installation's front
(`http://host.example/wfe/`). From the page, the reads are therefore `../../api/catalog`,
`../../api/nodes` and `../../api/catalog/publication/facts/<catalog-project>`. Do not write a
leading slash or a host: `/api/catalog` leaves the `/wfe/` route.

The fields the map needs (each response carries more; ignore what you do not use):

- `api/catalog`
  - `configured`, `repository` (`owner/name`), `web` (the catalog repository's page on the
    installation's Git host), `branch`, `head` (the catalog commit read).
  - `braindumps[]`: `id` (what grounds, suggestions and your evidence refer to; accept a `path` too), `path` (the file in the catalog), `title`, `excerpt`, `tags[]`,
    `updated.commit`, `projects[]` (ids of the projects it grounds), `published` (boolean: the
    catalog's public list names it, which is a selection, not a confirmed publication), and `rule`
    when a tag rule applies: `suggest` or `never` holds the rule's id, `selected` says whether the
    contract selects the braindump.
  - `projects[]`: `project` (the id), `registered`, `braindumps[]` (`id`, `title`: the agreed
    grounds, taken from the project's `because` in the installation's plan), `entry.source` and
    `entry.commit` (the project's repository and revision).
  - `links.suggestion.links[]`: an agent's suggestions; one with `state: "suggested"` and
    `kind: "add"` is an unanswered link between its `braindump` and its `project`.
  - `disclosure.projects[]`: `project`, `state` (`private`, `to be published`, `public`,
    `public without a statement`, `not stated`), `public[]` (`destination`, `commit`, `at`: the
    publication records).
  - `rules[]` (top level, not inside `disclosure`): the adopted rules with the owner's sentence
    (`id`, `source.braindump`, `source.sentence`).
- `api/nodes`
  - `state`, `source` (`kind`; `repository` and `commit` only when the templates come from the
    catalog),
    `catalog.templates[]`: `id`, `revision`, `name`, `type`, `description`, and `grounds[]`
    (`braindump`, `commit`, `passage`, `revision`, `kind`).
  - When `source.kind` is `cluster`, the templates come from a parent installation, which does not
    show its grounds: `grounds` is absent. That is *grounds not visible*, not *ungrounded*.
- `api/catalog/publication/facts/<catalog-project>`
  - `repositories[0]`: `source_rev`, `destination`, `public` (`public_commit`, `source_rev`,
    `published_at`; absent before a first publication), `selections[]` with `kind` (`tree`, `file`,
    `node`, …), `public` (the public path), `paths[]` and `status` (`public`,
    `public; source changed since`, `selected, not published yet`, `widening`). A selection of
    `kind: "node"` carries the template's `id` and `revision` instead of a path.
  - `problems[]`, `readAt`.
  - A failed read is a status other than 2xx with a JSON body `{"error": "…"}`; allow for a slow
    answer too.

## From the reads to the legend

The legend's states are the example's; the reads use their own words. One mapping that keeps the
three facts apart (change it if your legend differs):

| Kind | Intent | Selected | Published |
| --- | --- | --- | --- |
| braindump | `rule.never` → private; `rule.suggest` → meant to be public; no `rule` → unknown (a tag without an adopted rule states nothing) | a facts selection whose `paths[]` contains the braindump's `path` → yes; facts read and none → no; facts not read → unknown. Do not use `published` or `rule.selected` of `api/catalog` as a substitute | that selection's `status` starts with `public` → yes; otherwise no publication is recorded |
| node | unknown (nothing states a disclosure for a template; its grounds' state says nothing about it) | a facts selection with `kind: "node"` and the template's `id` → yes, with the mark `example r<revision>`; none → no; facts not read → unknown | as for a braindump |
| project | `disclosure.projects[].state`: `private` → private; `to be published`, `public` → meant to be public; `not stated`, `public without a statement` → unknown | unknown: none of the three reads carries a project's contract | `public[]` not empty → yes, with its `destination` and `commit`; empty → no publication is recorded |

A source link is built from `web`: on Gitea a file at a commit is
`<web>/src/commit/<commit>/<path>#L<line>`, and a commit is `<web>/commit/<commit>`.

- A project: its page in the installation is `../../#/ws/<workspace>` when the entry is `registered`
  and has a `workspace`; show `entry.source` (a clone address, not a page) and `entry.commit` as text.
- A node template: no page address is part of the three reads; show `source` (provider and commit).
- A ground carries a `passage` and a `commit`, not a line: link the braindump's file at that commit
  and show the passage.

## Missing data is not a negative fact

The three reads fail and lag independently. Draw what is established and say what is not:

| Situation | What the map shows |
| --- | --- |
| `api/catalog` fails or `configured` is false | no map; the reason |
| `api/nodes` fails | the map without nodes, and a note that nodes could not be read |
| `source.kind` is `cluster` (grounds withheld) | nodes without lines, and a note that grounds are not visible here |
| the facts read fails, is slow, or has no repository | *Selected* and *Published* are **unknown** for every braindump and node, with a note; never "not published" |
| a selection exists and `public` is absent | *Selected*: yes; *Published*: no publication is recorded |
| a project has no decision in your records | drawn under *Unclassified*, as "no decision" |
| a decision says `category: unclassified` | drawn under *Unclassified* with its reason: the classifier looked and the evidence did not decide |
| a decision names a project the installation does not have | listed apart as a decision without a project; not drawn as a project |
| a decision's evidence names a braindump that is gone | the reason is kept; the evidence is shown as no longer among the braindumps |
| your decisions file was projected from another catalog commit than `head` | the map names both commits and says the decisions may be behind (the page cannot tell older from newer, and any later catalog commit triggers this until the next refresh) |

The service answers a request for a file that does not exist below `local-views/` with the editor's
own page (status 200, HTML). Check the content type or parse result of your generated file, and
treat HTML as "missing".

## Your records

Kept in your catalog, not in this example and not in the core. Suggested place:
`views/catalog-map/`.

`classifications.yaml`: your categories, then one decision per project id.

```yaml
schema: views.catalog-map.classifications.v1
categories:
  - id: field-recording          # yours: rename, drop, add
    label: Field recording experiments
    means: trials of ways to record and loop natural sound
projects:
  tidepool:
    category: field-recording    # one category id, or unclassified
    reason: "The braindump asks to try a method for making ambience loops; it names no product."
    evidence: {braindump: shore-sounds, commit: "0000000000000000000000000000000000000000", line: 1}
```

`adoption.yaml`: what you started from.

```yaml
schema: views.catalog-map.adoption.v1
example:
  source: https://git.example/someone/mycatalog.git   # where you read the example: an address, or words when you have none
  path: view-examples/catalog-map
  commit: "1111111111111111111111111111111111111111"  # the revision you adopted
local:
  categories_renamed: {asset-technique-experiment: field-recording}   # example id: your id
  categories_dropped: [production]                                    # example ids you do not use
  categories_added: [field-trip]                                      # your ids the example does not have
implementation: local-views/catalog-map                # in your installation's source
```

There is no author field. Attribution is the Git history of `classifications.yaml`: the author of
the commit that last wrote a decision's `category` line (`git blame`) is who decided it.

## Refreshing and adopting again

Two different operations, both safe to repeat:

- **Refresh the decisions.** An agent re-reads the evidence and may rewrite only the entries whose
  `category` line an agent last wrote. An entry whose `category` line a person last wrote is a
  correction: it is kept as it is, and the agent may say in its commit message that it would have
  chosen otherwise. Decide "agent or person" from the Git author, with your installation's own
  convention for agent identities.
- **Adopt the example again** (the same revision, or a newer one). Never copy `example.yaml` over
  your records. Compare the example at the new revision with the one at the revision recorded in
  `adoption.yaml`; apply what changed upstream as a proposal to your own files; map example
  category ids through `local.categories_renamed`, and do not propose again what
  `local.categories_dropped` names; keep your category ids, labels and every decision. Then record the new revision. Adopting the same revision again changes nothing but
  confirms the record.

After either, project the decisions again (below) when `classifications.yaml` changed.

## Where the page lives

In your installation's source repository (your copy of the core), which a public derivative does
not carry:

```
local-views/<view>/            e.g. local-views/catalog-map/
  web/                         what a browser is served: index.html, your CSS and JavaScript,
                               and the generated decisions file
  <anything else>              the projection script, notes: stays in the source, is not served
```

A release built from a commit that has `local-views/<view>/web/` carries it as
`dist/local-views/<view>/`, and WFE serves it at `<wfe>/local-views/<view>/index.html`
(`scripts/wfe-release.sh`; `workflow_editor/docs/site.md`, *An installation's own pages*). The
files are read from the commit, so commit before building. A commit without the directory builds
the same release without it.

## Your decisions in the browser

WFE has no read for arbitrary catalog files, so the page cannot read `classifications.yaml` live.
Project it into one static file under `web/` (for instance `catalog-map.data.json`) with a small
script you keep beside `web/`:

- input: your catalog checkout and one catalog commit;
- output: the categories, each decision (category, reason, evidence reference), for each decision
  the Git author's name, date and commit of its `category` line and whether that author is an agent
  or a person by your convention, the catalog commit it was read at, and the example revision from
  `adoption.yaml`;
- no braindump text, no e-mail address and no credential. The file's shape is yours.

**Refresh operation**: after a change of `classifications.yaml` is committed in the catalog, run the
script with that commit, commit the regenerated file in the installation's source, and build and
activate a release from that commit. Write the exact command in your view's own README. The page
states which catalog commit its decisions come from and compares it with `head` of `api/catalog`.

## The optional Catalog link

`catalogLinks` in the installation's display settings adds a button to the Catalog page
(`workflow_editor/docs/site.md`). In `instance.toml`:

```toml
[[display.catalog_links]]
name = "My map"
url = "local-views/catalog-map/index.html"
```

then `agdevctl --config <instance.toml> display`, which writes it to the service's `site.json`
(`"catalogLinks": [{"name": "My map", "url": "local-views/catalog-map/index.html"}]`). The `url`
is a path below the service's own route: no scheme, no leading slash, no `..`. It takes effect on
the next page load. With no entry there is no button, and the page stays reachable by its address.

## Checking your result

- Open the page under both addresses of the service if you have both (own port, front route).
- Choose a project: its category, the reason, the evidence link (it opens your braindump at the
  cited commit and line), and who decided.
- Choose a grounded node and follow its ground to the braindump.
- Make the facts read fail (or look before it arrives): *Published* reads unknown.
- Remove the link and the directory: the Catalog page and its relation diagram are unchanged.
