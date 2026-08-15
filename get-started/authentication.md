---
title: Authentication — Anonymous vs. API Key Access
description: How the AnySearch search API handles anonymous and authenticated requests, quota policy, and invalid-key behavior.
---

# Authentication

The AnySearch search API (`/v1/*`) supports flexible authentication. You decide whether to send an API key based on where you are in your product lifecycle.

| Mode | Header format | Quota & rate limit policy |
|---|---|---|
| Anonymous | No `Authorization` header | Rate-limited per client IP and metered against the daily free quota |
| Authenticated | `Authorization: Bearer YOUR_ANYSEARCH_API_KEY` | Billed against the paid quota attached to the key, with higher concurrency limits |

**Heads up:** if you send an `Authorization` header but the key is invalid, disabled, or expired, the gateway returns `401 Unauthorized` or `403 Forbidden` — it will not silently fall back to anonymous mode.

## Getting a key

Create a free API key at [anysearch.com/console/api-keys](https://anysearch.com/console/api-keys). Priority order for the Skill plugin: CLI flag > `.env` file > environment variable > anonymous access. See [Skill Installation](../skill/installation.md) for the full setup flow.

## Related errors

Invalid or expired keys surface as `invalid_api_key`, `invalid_auth_header`, or `expired_api_key` — see the full list on [Error Codes](../api-reference/error-codes.md).
