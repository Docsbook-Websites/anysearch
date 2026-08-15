---
title: FAQ — AnySearch Product, Search Quality, and Privacy
description: Answers to the most common AnySearch questions on product capabilities, search quality, and privacy and security.
---

# Frequently Asked Questions

From product capabilities to integration setup, here are the questions we hear most often.

<!-- widget:accordion -->

### What is AnySearch?

AnySearch is search infrastructure built for AI Agents. It pulls together data from many vertical domain sources and gives your Agent one place to search it all — structured results, ready to use.

### How is AnySearch different from other search tools?

Regular search only covers public web pages. But a lot of valuable information isn't on the web at all — stock prices are computed in real time, legal documents live in paid databases, code snippets are spread across millions of repos. Web search can't reach any of this. It's not a gap — it's a wall.

AnySearch goes straight to where this data lives. You get back structured results, not a list of links.

### What makes AnySearch different from other AI search products?

Most AI search products use the same search engine under the hood — different models process the same web pages.

AnySearch is built differently: one query searches across multiple vertical domain sources at once, routed by intent, merged, and ranked, then returned as the best result. It supports MCP and Skill out of the box, with output formatted as structured Markdown for Agents.

### What domains does AnySearch cover?

Finance, academia, code, security, business, medical & health, patents, energy, environment, agriculture, travel, gaming — and growing. See the full [Tags & Params](./api-reference/tags-and-params.md) reference.

### How does AnySearch evaluate information quality?

Results are scored on authority, diversity, and freshness, then ranked using a cross-source fusion ranking algorithm. What comes back first is what's most reliable and most suitable for Agents.

### How fresh are the search results?

AnySearch detects freshness intent from your query and routes to real-time data automatically — as fast as second-level sync.

### Does AnySearch provide structured outputs?

Yes. Every response is structured. Through MCP or Skill, you get clean, compact Markdown that Agents can use directly — no parsing needed: fewer results, same or better coverage, much lower token cost. Through the REST API, you get standard JSON with a consistent schema no matter where the data comes from.

### How does AnySearch work with AI Agents?

Two integration options, with identical features:

- **MCP Server** — remote, no local setup. One line of config for OpenCode, Claude Desktop, Cursor, Codex, and more. See [MCP Server Installation](./mcp/installation.md).
- **Skill Plugin** — runs inside your Agent. Supports Python, Node.js, PowerShell, Bash. See [Skill Installation](./skill/installation.md).

The flow: your Agent recognizes user intent → sends a query → AnySearch handles routing, merging, and ranking → the Agent gets structured results and keeps going. The REST API (`POST /v1/search`) is also available directly, but for Agents MCP or Skill is recommended.

### Are search queries stored?

No. AnySearch collects only the minimal usage data needed to improve the product — no personal or query data is stored. Searches are never used for training and never shared with anyone. Everything is encrypted in transit.

### How does AnySearch protect sensitive searches?

Everything is encrypted end to end. Search content is never stored — it's processed and discarded promptly. Credentials are transformed irreversibly. At every layer — transport, processing, storage — sensitive data cannot be recovered or leaked.

### How do I get started?

The fastest way: add the MCP config to your AI tool — one line of JSON and you're searching. See [Quick Start](./get-started/quickstart.md). You can also call the API directly, no sign-up needed, with free quota out of the box.

<!-- /widget -->
