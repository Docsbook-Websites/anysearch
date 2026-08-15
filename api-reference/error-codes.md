---
title: Error Codes — AnySearch API Status Reference
description: Every HTTP status and error symbol the AnySearch gateway can return, with what causes it and how to handle it.
---

# Error Codes

Every error response includes a `request_id` field. `429` responses also carry `Retry-After` and `X-RateLimit-*` headers.

<!-- widget:accordion -->

### 400 invalid_request

Invalid request body, empty query, or illegal values for `tag` / `zone` / `format`.

### 400 invalid_extract_url

Extract tool: `url` is missing, scheme is not http/https, URL parsing failed, or host is missing.

### 401 invalid_api_key

API key does not exist, is disabled, or is not bound to an account.

### 401 invalid_auth_header

Authorization header format is invalid (not `Bearer xxx`).

### 402 daily_free_quota_exhausted

Anonymous IP daily free quota exhausted; the response includes auto-registered account credentials (username / password / api_key) that can be used immediately.

### 402 quota_exhausted

Paid quota for the API key or account exhausted for the current billing period; `data` contains `quota_limit` / `quota_used` / `quota_remaining`.

### 402 user_daily_quota_exhausted

Registered user's daily free quota exhausted and no paid plan purchased; resets next day or purchase a plan.

### 403 expired_api_key

API key has expired.

### 403 private_capability_not_enabled

The requested private capability is not enabled for this API key; contact support to activate.

### 403 account_disabled

Account associated with the API key is disabled.

### 415 extract_unsupported_content

Extract target response `Content-Type` is not `text/html`.

### 429 rate_limit_exceeded_user

Account-level aggregate rate limit hit (all keys under the same account are counted together).

### 429 rate_limit_exceeded

Per-key or per-IP rate limit hit; `data` contains `retry_after` / `limit` / `remaining` / `reset_at`.

### 500 internal_error

Internal server error, safe to retry.

### 502 extract_fetch_failed

Extract fetch failed: DNS / TCP / TLS / body read / HTML parsing error (non-timeout).

### 502 extract_upstream_error

Extract target returned a non-2xx HTTP response.

### 503 quota_check_failed

Quota check dependency unavailable, retry after a brief back-off.

### 503 guard_evaluate_failed

Guard evaluation dependency (KeyStore / rate limiter, etc.) returned an error, retry after a brief back-off.

### 503 capability_temporarily_unavailable

The requested capability (including underlying plugin backends) is temporarily unavailable, retry with back-off.

### 503 service_unavailable

Service temporarily unavailable, retry with back-off.

### 504 extract_timeout

Extract fetch timed out (default 30s limit).

<!-- /widget -->

## Related

- [Response Format](./response-format.md) — Where `request_id` and error bodies come from
- [Authentication](../get-started/authentication.md) — Avoiding `401`/`403` on the auth path
