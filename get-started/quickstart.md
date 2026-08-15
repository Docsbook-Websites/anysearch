---
title: Quick Start — AnySearch API in Two Steps
description: Get an API key and fire your first AnySearch request in under five minutes, with or without authentication.
---

# Quick Start

Unified search infrastructure for AI. Two steps to plug AI-grade search into your app: grab an API key from the console (or skip it and try the free anonymous tier), then fire your first search request.

**API Base URL:** `https://api.anysearch.com`

<!-- widget:stepper -->

### Try it anonymously

No account needed. Anonymous requests are rate-limited per client IP and metered against the daily free quota.

```bash
curl -X POST https://api.anysearch.com/v1/search \
  -H "Content-Type: application/json" \
  -d '{
    "query": "Go 1.26 release notes",
    "tag": "code.doc",
    "params": {"library": "golang"},
    "max_results": 10
  }'
```

### Get an API key (optional but recommended)

Create a free key at [anysearch.com/console/api-keys](https://anysearch.com/console/api-keys). Authenticated requests are billed against your paid quota with higher concurrency limits.

### Send an authenticated request

Replace `YOUR_ANYSEARCH_API_KEY` with your real key.

```bash
curl -X POST https://api.anysearch.com/v1/search \
  -H "Authorization: Bearer YOUR_ANYSEARCH_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "Go 1.26 release notes",
    "tag": "code.doc",
    "params": {"library": "golang"},
    "max_results": 10
  }'
```

<!-- /widget -->

AI agents handle `tag` and `params` routing automatically via MCP or Skill — you only need to think about them for direct API usage.

## Next steps

- Read [Authentication](./authentication.md) to understand anonymous vs. authenticated quota policy.
- Browse [Endpoints](../api-reference/endpoints.md) for the full request/response contract.
- Prefer agent integration? Jump straight to [MCP Server](../mcp/installation.md) or [Skill Plugin](../skill/installation.md) — both skip manual tag/param selection entirely.
