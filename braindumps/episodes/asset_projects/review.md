_Review by summoner-agent, 2026-11-17, catalog 69d5651f189f256867b5389499abcc6a59902989._ Refreshes the review at 94cd4eb; the braindump itself is unchanged (fb518cd).

The braindump `asset_projects` has four bullets: a general policy for public asset-making projects, and one line each for agsfx, gimmickimg and lowerpoly. The three projects are in plan agdev-a (all `adopted`) and the plan now grounds each in this braindump (`wfe catalog why agsfx` shows it); the earlier review said they had no ground. This review writes no link. Nothing (run or conversation) cites the braindump yet.

| What it asks | What exists now | Where |
|---|---|---|
| agsfx turns AI-model and agent sound-effect making into workflows; covers single waveform creation and spatial placement, experimenting widely on SFX methods | Partly real. Workflows `create`, `research`, `improve-tools`, `freework`, `publication-edit`; its purpose is choosing between procedural/DSP and generative means case by case. Completed runs: create 5, research 2, freework 3. Pack `protoprey_locations` (20 effects, CC0) was delivered. Its README limits effects to short clips and loops, not music or speech. | `wfe projects show agsfx`; README; `wfe projects runs agsfx` |
| (agsfx) spatial placement of sound effects | Not seen. The README and workflow list mention no spatial placement or spatialisation; the "where it plays (scene, surface, distance)" is only a request field. Not checked in lab/ experiments. | agsfx README |
| gimmickimg experiments with expressions based on a flat image and turns them into workflows | Real. Workflows `freework` and `partial-animation`; 23 completed freework runs; deliverable is a Godot scene animating a still (depth, segmentation, matting, clean plate), with a delivery contract (`docs/delivery.md`) and findings under `wedo/`. | `wfe projects show gimmickimg`; README; runs |
| lowerpoly experiments with mesh-count reduction, mainly for real-time rendering, and turns them into workflows | Real, as research. Workflows `freework` and `lod-chain`; 5 freework and 3 lod-chain runs completed; 9 inputs in the first experiment; LOD chains reproduced for eagle_beak and wolf_tongue; Godot 4.7.2 headless load verified. Its README says it is a research pipeline, not a packaged tool. | `wfe projects show lowerpoly`; README; runs |
| Public asset projects publish generalizable workflows, findings and scripts as far as possible | Partly. The plan includes `publisher` (turns internal work into public material, with a deterministic publication tool), and agsfx has a `publication-edit` workflow (one run completed). gimmickimg and lowerpoly keep reusable findings in `wedo/`. Whether anything from these three is actually public was not established. | `wfe projects show publisher`; agsfx runs |
| Care that useless-to-publish information and personal information do not enter the public workflow, since the projects depend on local compute | Not established. A publication path exists (publisher, `publication-edit`), but no record read here shows the filtering of local-resource-dependent or personal information. The projects themselves mention ComfyUI availability and a specific machine's build times in READMEs/findings. | agsfx README ("Limits"); lowerpoly README ("Build cost") |

## Not real / open
- No evidence for agsfx spatial placement.
- The publication-hygiene care is a wish with no recorded mechanism that checks it.
- No open challenges name agsfx, gimmickimg or lowerpoly as such; open challenge ch-0004 ("animation over window", gimmickimg) is a wish for window-scene animation, not about publication or this braindump's policy.

## Not checked
- Contents of the agsfx, gimmickimg and lowerpoly runs beyond their state; whether any concerns spatial placement.
- Whether any material is in fact published, and what `publisher` did for these three.
- Whether the `public` aspects (the word "公開") mean public source repositories or public deliverables.

