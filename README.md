# mycatalog (iwaag)

The public part of iwaag's **mind repository** for [agdev](https://github.com/iwaag/agdev): the
projects iwaag shares, for anyone who runs their own agdev installation and wants to summon them.

- `catalog.yaml` (`ag.catalog.v1`): the shared projects. Each entry names the project id, its Git
  `source`, a recommended `commit`, one line on what it is for, the core `roles` it can fill, and
  `because` — braindumps of this mind that ground it. Those braindumps are not published here; the
  references only say that grounds exist.
- `mind.yaml` (`ag.mind.v1`): whose mind this is.

The name is fixed: a user's shared projects are found at `<user>/mycatalog`, so this one is
`iwaag/mycatalog`. Naming the user is therefore enough to import iwaag's development style into
an agdev installation: `wfe summon style iwaag`, or *Import a development style* on the Mind page.

## Summoning from the catalog

An installation's projects are described by a summonplan (`ag.summonplan.v1`) in that installation's
own mind repository. To take a project from this catalog, copy its `project`, `source`, `commit` and
`roles` into a plan entry with `state: summoned`, and write `because` from your own braindumps (or
leave it empty). Then `wfe mind plan put` and `wfe summon apply` (or `agdevctl bootstrap-projects
--plan <file>` on a new installation) fetch the public repository at that commit, with its
submodules, into your installation's Gitea and wire the roles. See agdev's
`workflow_editor/docs/mind.md` and `workflow_editor/docs/summon.md`.

A role is filled by one project per installation. Public repositories need no credential.

The **summoner** (listed here too) does this for you: request its `propose` workflow with a
braindump, and it reads this catalog, proposes the entries your braindumps call for with the
reasons, and applies the plan once you agree. A new agdev installation receives it first
(`agdevctl bootstrap-projects` with no plan).

## Provenance

This repository is an edited selection of a private mind repository: the catalog and `mind.yaml`,
with the owner's public account name. Its history is its own. Licence: CC0 1.0 (`LICENSE`).
