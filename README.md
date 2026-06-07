# FleetDeck — Preview

> Sanitized public preview. Real fleet data never leaves the machine; everything
> below is illustrative fake data.

**Fleet Deck** is a tiny local-only dashboard for supervising multiple autonomous
AI coding sessions coordinated through a shared file blackboard. One page,
auto-refreshing, zero dependencies (Python stdlib), strictly read-only.

## What it shows

| Panel | Example (fake data) |
|---|---|
| Worker cards | `alpha — WORKING — hb 3m ago` / `bravo — BLOCKED — hb 41m ago — STALE` |
| Heartbeat units | `alpha__buildout · running · iter 7 · budget 2/12` |
| Stop flags | 🛑 banner when a supervisor halts a unit |
| Questions queue | the curated "needs a human decision" digest |
| Supervisor log | last two oversight-cycle entries |

## Design highlights

- **Localhost-only by construction** — bind is hard-coded to `127.0.0.1`; this is
  private ops tooling, not a deployable app.
- **No routes that touch the filesystem from user input** — fixed allowlist of
  files, so no traversal surface.
- **Everything escaped** — blackboard files are written by other agents and are
  treated as untrusted input.
- **Read-only** — the dashboard renders the blackboard; it never writes to it.

Source code is private.
