_Review by summoner-agent, 2026-11-17, catalog 10db3ade38f3fa25a514feff71322e8d6e78a5c3._

This refreshes the earlier review (70116c9). The braindump gained a fourth sentence, about `front`, and now grounds `front`, `cagent`, `forge` and `archsage` in plan agdev-a. It still asks for nothing to be built: it records an evaluation of four support agents and some ideas for redesign. So this review says whether each statement matches the records, and what they show about use.

| What the braindump says | What exists now | Where |
|---|---|---|
| archsage was set up to think and answer from knowledge accumulated on the cluster, but is hardly used so far; its value may grow with the knowledge, so it is under careful evaluation | The project exists, adopted in agdev-a. Its runs include discuss (12), converse, study (5), consult, freework and backfill-wedo. No open challenge. | `wfe projects show/runs archsage` |
| forge was set up to aggregate what is learned from asset-generation requests, but people often ask the individual projects directly; design under reconsideration | The project exists, adopted. Runs: provide (19, one cancelled), discuss, converse, freework, develop-capability, publication-edit. No open challenge. | `wfe projects show/runs forge` |
| cagent gathers cluster information and operates the environment (e.g. with ansible) when needed; agdev's mechanisms changed since its design, so it needs rethinking | The project exists, adopted. Runs: change, context (11), consult, develop (4), report (3), scan (2), freework (2). No open challenge. | `wfe projects show/runs cagent` |
| front was made to talk with the human and do work on their behalf, but that role has moved to ponderer and summoner and front is little used now; it could be redesigned as a communication role for remembering the user's preferences and for entertainment that raises motivation | New in this version. The project exists, adopted (at 41924e7). Its intent still reads: be the Developer's conversational entrance, carry requests through, and remember preferences. Workflows: converse, discuss, freework, lesson. Published runs: converse 59, discuss 14, freework 1, lesson 1, all completed. The role the braindump says moved is present: `ponderer` fills facilitation and conversation-archive, and `summoner` is in the plan (`wfe summon status`). The proposed redesign (preference memory, entertainment-oriented) is not in front's intent or workflows. No open challenge. | `wfe projects show/runs front`, `wfe summon status` |

## What the records say about the statements
- All four projects are present and have run history, so none is an empty shell. Run counts show only that runs were made, not who asked, when, or whether the answers were useful. "Not much used" is therefore neither confirmed nor contradicted. For front, 59 converse runs exist; whether they are recent was not read.
- The claim that front's role passed to ponderer and summoner fits the plan: those two are adopted and ponderer holds facilitation and conversation-archive roles. front holds no role.
- For forge, many `provide` runs sit beside `discuss`/`converse` runs; whether these are the "direct requests" meant was not established.

## Not real / open
- Nothing is decided. The evaluation of archsage, the reconsideration of forge and cagent, and the redesign idea for front have no recorded outcome or criteria (what would count as "useful enough"). No challenge names any of the four.
- front's recorded intent does not yet reflect the redesign idea; it is an idea ("might be good"), not a plan.
- No run or conversation cites this braindump yet.

## Not checked
- Contents and dates of any run of the four projects, who requested them and why.
- Whether archsage's knowledge areas are growing.
- Whether front's memory of preferences exists in any form.
- Overlap with other adopted projects' workflows.

The braindump is tagged `public, style` (metadata ea49147, set by the owner); no tag change is proposed. A review is someone's reading of how far a braindump has become real, at its date; check it against the present state before relying on it.
