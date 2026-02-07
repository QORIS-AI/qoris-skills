---
name: qoris-memory
description: Teaches Claude to route memory to Qoris MCP instead of claiming to remember internally. Use when Qoris MCP is connected and user expects persistent memory across conversations. Do NOT use for knowledge base search (use qoris-knowledge instead).
---

# Qoris Memory Skill

This skill teaches Claude how to interact with the Qoris Memory Control Plane via MCP. Qoris manages persistent, governed memory externally, ensuring consistency across models.

## Core Principle

When Qoris is available, treat memory as external and authoritative. Do not claim to "remember" things yourself.

## Instructions

### When Qoris MCP is Connected

1. **Do not claim to "remember" things yourself** — Claude should never say "I'll remember that" or imply internal memory. Instead, say you'll save it to Qoris (or similar).

2. **After generating a response, pass context to Qoris via MCP** — After each meaningful exchange, use the Qoris MCP tools to persist user input and your output. Let Qoris decide whether memory should be created, amended, or ignored.

3. **Let Qoris decide** — Call `save_memory` (or `get_memories` first to check existing context) with the relevant content. Do not pre-filter aggressively; Qoris handles governance.

4. **Treat memory as external and authoritative** — When the user asks about prior context, use `get_memories` to retrieve from Qoris. Do not rely on in-conversation recall.

### MCP Tools to Use

- `save_memory` — Save new information to workspace memory (content, optional agent_id, agent_name)
- `get_memories` — Retrieve all workspace memories (limit, offset)
- `update_memory` — Update an existing memory (memory_id, content)
- `delete_memory` — Delete a memory (memory_id)

### Best Practices

- Save important preferences, decisions, and context after exchanges
- Retrieve memories at the start of conversations when continuity matters
- Use clear, concise content when saving; avoid redundant or trivial saves

## Troubleshooting

**MCP calls fail:** Verify Qoris MCP is connected and authenticated. Check Settings > Extensions (Claude.ai) or MCP configuration (Claude Code).

**Memory not persisting:** Ensure `save_memory` is called after responses. The tool returns success; if it fails, surface the error to the user.
