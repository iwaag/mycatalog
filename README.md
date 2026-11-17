# mycatalog (iwaag)

The published part of iwaag's **catalog** for [agdev](https://github.com/iwaag/agdev): the
projects iwaag shares, for anyone who runs their own agdev installation and wants to summon them.

A catalog is a user's record of what drives their development (braindumps: what is wanted and why),
how far that became real (reviews), and where the results are found. iwaag's whole catalog lives on
a private Git service. This repository holds the part chosen for publication.

- `projects.yaml` (`ag.projects.v1`): the shared projects. Each entry names the project id, its Git
  `source`, a recommended `commit`, one line on what it is for, the core `roles` it can fill, and
  `because`: the braindumps of this catalog that ground it (see below).
- `mycatalog.yaml` (`ag.mycatalog.v1`): whose catalog this is.
- `braindumps/episodes/<name>/`: the braindumps iwaag tagged `public`, each as its own files only
  (`braindump.md`, `metadata.yaml`, and `review.md` where there is one). The braindumps are
  iwaag's words; a review is a summoner agent's reading of how far a braindump has become real.
  Braindumps and reviews are not edited for publication, except that a review is written in a
  public form. Not every braindump is published, so some `because` references of
  `projects.yaml` point at braindumps that are not here.
- `rules.yaml` (`ag.catalog-rules.v2`): the rules iwaag adopted from their own words: which tags are
  published (`public` is suggested for publication, `private` is never published) and which
  projects are shared (`agsfx`, `lowerpoly`, `gimmickimg`).

**How to read the reviews.** They cite `wfe` commands, plans and runs of iwaag's own agdev
installation, and commit ids of internal repositories. An outside reader cannot reach them. They
are iwaag's evidence for what was said at the time, not something to follow or reproduce.

The name is fixed: a user's catalog is found at `<user>/mycatalog`, so this one is
`iwaag/mycatalog`. Naming the user is therefore enough to import iwaag's development style into
an agdev installation: `wfe summon style iwaag`, or *Import a development style* on the Catalog page.

Earlier this repository had `catalog.yaml` and `mind.yaml`. They were replaced by the two files
above; an agdev core older than that change cannot read this repository and says so.

## Summoning from this catalog

An installation's projects are described by a summonplan (`ag.summonplan.v1`) in that installation's
own catalog. To take a project from `projects.yaml`, copy its `project`, `source`, `commit` and
`roles` into a plan entry with `state: summoned`, and write `because` from your own braindumps (or
leave it empty). Then `wfe catalog plan put` and `wfe summon apply` (or `agdevctl bootstrap-projects
--plan <file>` on a new installation) fetch the public repository at that commit, with its
submodules, into your installation's Gitea and wire the roles. See agdev's
`workflow_editor/docs/mycatalog.md` and `workflow_editor/docs/summon.md`.

A role is filled by one project per installation. Public repositories need no credential.

The **summoner** (listed here too) does this for you: request its `propose` workflow with a
braindump, and it reads this catalog, proposes the entries your braindumps call for with the
reasons, and applies the plan once you agree. A new agdev installation receives it first
(`agdevctl bootstrap-projects` with no plan).

## Provenance

This repository is an edited selection of a private catalog: `projects.yaml`, `mycatalog.yaml`, the public
braindumps with their reviews and metadata, and `rules.yaml`,
with the owner's public account name. Its history is its own. Licence: CC0 1.0 (`LICENSE`).
