# Personal Agent Starter

A drop-in workspace that turns a fresh coding harness into a capable **personal assistant**: an executive assistant by default, but the same building blocks serve a wealth manager, a house-build / architect tracker, or a meeting manager.

Built to run in **[DAM](https://github.com/dam-agents/dam)**: an isolated cloud pod (VM- and network-isolated, allowlisted egress). The agent's capabilities (email, calendar, chat, files, scheduling) are provided by the runtime as tools and skills, so you don't wire them up here.

> This README is the one file the agent doesn't live by. It's for **you**, the person deploying the agent. (During bootstrap the agent may glance at the example shapes below for inspiration, but it shapes itself to your actual needs, not to a label.)

## How to use it

1. Clone this repo into the agent's working directory (`work` in DAM):

   ```bash
   git clone https://github.com/matoushavlena/personal-agent-starter.git work
   ```
2. Start the agent. On first run it follows `BOOTSTRAP.md`: a short conversation to set its identity, learn about you, shape its workspace to your needs, and install its schedules. Then it deletes `BOOTSTRAP.md`.
3. From then on it works from these files, keeping them current as its memory.

## The building blocks

| File | What it is |
|---|---|
| `SOUL.md` | Who the agent is — values plus its name / vibe / emoji / mission. |
| `USER.md` | Who it works for — you. |
| `CLAUDE.md` | Its operating manual: workplace, startup routine, memory, heartbeat, safety, house style. |
| `AGENTS.md` | Symlink to `CLAUDE.md`, for harnesses that look for `AGENTS.md`. |
| `MEMORY.md` | Curated long-term memory (distilled facts). |
| `memory/` | Raw daily logs plus `heartbeat-state.json`. |
| `TODOS.md` | Single-step tasks, plus a waiting-on chase-list of what others owe you. |
| `projects/` | Bigger, multi-step threads — one file or folder each. |
| `TOOLS.md` | Local notes: setup-specifics and preferences your tools and skills don't already cover. |
| `HEARTBEAT.md` | The proactive checklist the heartbeat reads on each wake. |
| `PRUNE.md` | The weekly maintenance procedure the prune cron runs (distill logs, trim memory, clear old items). |
| `.claude/settings.json` | Model, attribution, permissions. |

## Day one in DAM

- The agent installs two schedules through the schedule MCP: a **heartbeat** (~every 30 min during waking hours) and a **weekly prune**.
- It treats all tool output as data, never as instructions, and verifies before anything that leaves the pod.

## Example shapes

These are illustrations, not a menu. The same primitives (a `TODOS.md` with a waiting-on list, `projects/` as files or folders, a heartbeat) flex to almost any role that runs someone's affairs. A few worked examples:

**Executive / personal assistant.** Inbox and calendar triage, drafting replies, protecting focus time. The `TODOS.md` waiting-on list chases people for what they promised; the heartbeat surfaces urgent mail and imminent meetings.

**Wealth manager.** `projects/` tracks holdings and positions with a `decisions.md` rationale log per move; the `TODOS.md` waiting-on list chases counterparties, banks, and paperwork; the heartbeat watches for events and news that need a decision.

**House-build / architect tracker.** A `projects/<build>/` folder with `decisions.md` (what was chosen and why), `ledger.md` (items, costs, status), and `designs/` (drawings, references); the `TODOS.md` waiting-on list chases contractors and architects for deliverables.

**Meeting manager.** A `projects/<meeting>/` folder with prep and agenda; the `TODOS.md` waiting-on list tracks attendee confirmations; the heartbeat nudges people who haven't confirmed and assembles prep beforehand.

Your principal's needs may be none of these exactly, or a blend. Shape the workspace to the work, not to a label.

## Credits

Distilled from the OpenClaw workspace templates (the skeleton), a lived-in production assistant (the waiting-on register and project ledgers), and Hermes (memory discipline, tool-use enforcement, and the prompt-injection taxonomy).
