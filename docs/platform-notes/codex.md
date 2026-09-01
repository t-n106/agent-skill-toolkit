# Codex Platform Notes

This file maps platform-neutral concepts in the toolkit to Codex-specific runtime controls.

The skills themselves intentionally avoid Codex-specific parameter names so they can be reused in other agent runtimes. Treat this document as an adapter note, not as part of the normative skill policy.

## Context inheritance

The platform-neutral policies use three concepts:

- **No inheritance** — start the child/reviewer from fresh conversational context and provide a bounded task packet plus authoritative artifacts.
- **Limited inheritance** — inherit only the smallest recent conversation window that is genuinely task-critical.
- **Full inheritance** — inherit broad conversation history only when it cannot reasonably be reconstructed from artifacts and a bounded packet.

For Codex runtimes that expose `fork_turns`, the intended mapping is:

| Toolkit concept | Codex example |
|---|---|
| No inheritance | `fork_turns: "none"` |
| Limited inheritance | a small positive `fork_turns` value |
| Full inheritance | `fork_turns: "all"` |

The toolkit policy still applies regardless of the exact runtime syntax: prefer no inheritance, use limited inheritance only when recent conversation is itself task-critical, and treat full inheritance as exceptional.

## Portability rule

If Codex adds, removes, or renames a runtime control, update this platform note rather than changing the platform-neutral skill unless the underlying orchestration concept itself changes.
