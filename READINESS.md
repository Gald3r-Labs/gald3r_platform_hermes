# gald3r Readiness Report — Hermes Agent (Nous Research)

> An honest accounting of how much of the gald3r framework installs natively on this
> platform, what degrades to an approximation, and what has no native home yet.
> Generated from a live documentation crawl on 2026-06-02.

**Overall readiness: ✅ Full.** Hermes Agent is a self-improving CLI/TUI coding agent with a
closed learning loop. Every gald3r layer — commands, rules, agents, skills, and hooks — lands
on a native mechanism, and MCP is a first-class client as well. gald3r installs here without
approximation.

## C.R.A.S.H. capability grid

| | Capability | Native? | What gald3r gets here | The gap |
|---|---|:---:|---|---|
| **C** | Commands | ✅ | Slash commands + `bundles` (group skills behind one `/<bundle>` command) + `quick_commands` (exec/alias shortcuts); plugins can register commands | None — gald3r's `@g-*` set installs as native slash commands, and bundles package them |
| **R** | Rules | ✅ | Auto-discovered Context Files (`.hermes.md`, `AGENTS.md`, `CLAUDE.md`, `.cursorrules`) + `SOUL.md` identity + built-in `MEMORY.md`/`USER.md` | None — gald3r rules load as first-class context files; `AGENTS.md`/`CLAUDE.md` honored verbatim |
| **A** | Agents | ✅ | `delegate_task` spawns child agents with isolated context + restricted toolsets; `max_concurrent_children` / `max_spawn_depth` config; `/personality` presets | Delegation depth caps at 1–3 — gald3r's `g-agnt-*` roles map cleanly within that bound |
| **S** | Skills | ✅ | Native `SKILL.md` engine (agentskills.io standard) under `~/.hermes/skills/`; agent authors its own via `skill_manage`; `external_dirs` shares libraries | None — gald3r skills install as-is; `hermes curator` even helps with library hygiene |
| **H** | Hooks | ✅ | `config.yaml` shell hooks + plugin hooks via `ctx.register_hook()`; 11 events incl. `pre/post_tool_call`, `pre/post_llm_call`, `on_session_start/end`, `subagent_stop` | First-use TTY consent (or `--accept-hooks`) required — gald3r's `g-hk-*` wiring fires once allowlisted |

_Legend: ✅ native · ⚠️ partial / approximated · ❌ no native mechanism · ❓ unverified_

**Beyond C.R.A.S.H. — MCP: ✅** Native MCP client over stdio and HTTP, with selective tool
loading, server-initiated sampling, and auto-reload on config change (`hermes mcp
add/list/test/serve`). Hermes can also run *as* an MCP server, so gald3r's MCP backend connects
in both directions.

## Adoptable extras (non-C.R.A.S.H.)

Platform-native strengths gald3r can lean on, and which need wiring:

| Feature | Status | gald3r fit |
|---|:---:|---|
| Self-improving closed learning loop (agent authors skills via `skill_manage`) | ✅ present | Procedural-memory growth complements gald3r's static skill set |
| `hermes curator` review cycles (status/run/backup/rollback/pause/pin/archive) | ✅ present | Drops straight onto gald3r skill-library hygiene |
| `bundles` packaging primitive | ⚙️ needs customization | Bundle a set of gald3r skills behind one slash command |
| Plugin system (general / memory providers / context engines) | ⚙️ needs customization | Extension surface for gald3r tools, memory, and context assembly |
| Gateway mode + cron (non-interactive runs) | ⚙️ needs customization | Drives gald3r scheduled / headless workflows |
| 60+ built-in tools/toolsets | ✅ present | The unit MCP servers and plugins plug into; no gald3r work required |

## The ceiling, and what's beyond it

gald3r runs at full strength on this platform — commands, rules, agents, skills, and hooks all map onto native mechanisms, so the framework installs without compromise. As third-party adaptation goes, this is the high end: nothing here has to be approximated.

But adaptation, however clean, is still gald3r living as a guest inside someone else's tool. The native build goes further — **gald3r_agent**, running on the **gald3r throne** over the **gald3r_world_tree** — where these primitives aren't mapped onto a host, they *are* the substrate. Same framework, no host in between.

> ### gald3r_agent — coming soon. 🌳

---

<sub>Capabilities verified against the platform's official documentation on 2026-06-02, and
re-verified each release via the gald3r platform-docs crawl. This report describes gald3r's
third-party adaptation surface; it is not an endorsement or critique of the platform itself.</sub>
