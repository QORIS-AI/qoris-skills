# Qoris Skills for Claude

Skills that teach Claude how to use the Qoris MCP (Model Context Protocol) server for memory and knowledge management.

## Skills Included

| Skill | Description |
|-------|-------------|
| **qoris-memory** | Routes memory to Qoris instead of claiming internal recall. Use when Qoris MCP is connected and user expects persistent memory. |
| **qoris-knowledge** | Searches the Qoris project knowledge base. Use when user asks about docs, uploaded content, or needs synthesized answers. |

## Prerequisites

- Qoris MCP server connected (API key or OAuth)
- A Qoris project with workspace access

## Installation

### Claude.ai

1. Download the skill folder:
   - Clone: `git clone https://github.com/qoris/skills`
   - Or download ZIP from Releases
2. Open Claude.ai > Settings > Capabilities > Skills
3. Click "Upload skill"
4. Select the skill folder (e.g. `qoris-memory` or `qoris-knowledge`) — zip if needed
5. Enable the skill
6. Ensure Qoris MCP is connected (Settings > Extensions)

### Claude Code

1. Clone or download this repo
2. Copy the skill folder to Claude Code's skills directory
3. Enable the skill
4. Ensure Qoris MCP is in your config

## Quick Test

**Memory:** "Remember that I prefer dark mode for all UI." — Claude should save to Qoris via MCP, not claim internal memory.

**Knowledge:** "Search our knowledge base for authentication setup." — Claude should call `search_knowledge` and return synthesized answer with sources.

## MCP Server

- URL: `https://mcp.qoris.ai/mcp`
- Auth: API key (query param or header) or OAuth 2.0
- Docs: https://docs.qoris.ai/getting-started/authentication
