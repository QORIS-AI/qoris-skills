---
name: qoris-knowledge
description: Teaches Claude how to search the Qoris project knowledge base via MCP. Use when user asks questions about project documentation, wants to find information in uploaded documents, or needs answers synthesized from the knowledge base.
---

# Qoris Knowledge Skill

This skill teaches Claude how to use the Qoris knowledge search capability via MCP. Qoris indexes project documents, webpages, and knowledge items for semantic search with AI-powered synthesis.

## Core Principle

When the user needs information from project documentation or knowledge base, use `search_knowledge` instead of guessing or claiming uncertainty.

## Instructions

### When to Use

- User asks about project documentation, specs, or processes
- User wants to find information in uploaded documents or knowledge items
- User needs a synthesized answer with source citations
- User mentions "search the knowledge base," "what does the docs say," "find in our docs"

### MCP Tool to Use

- `search_knowledge` — Search the project's knowledge base. Returns a synthesized answer with sources.

Parameters:
- `query` (required) — The search query. Use at least 2 words for better results.
- `context` (optional) — Conversation context to improve relevance.

### Best Practices

- Use specific, detailed queries (2+ words minimum)
- Include context when the question is ambiguous
- Present the synthesized answer and cite sources when relevant
- If results are insufficient, suggest refining the query or adding more knowledge to the project

## Troubleshooting

**No results:** The project may have limited knowledge. Suggest the user upload documents or add knowledge items in Qoris.

**Irrelevant results:** Refine the query with more specific terms. Use the `context` parameter to narrow scope.
