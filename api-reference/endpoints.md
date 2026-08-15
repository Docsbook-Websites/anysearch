---
title: API Endpoints — AnySearch Unified Search
description: The POST /v1/search endpoint, its request parameters, and a live try-it playground for the AnySearch API.
---

# API Endpoints

<!-- widget:api -->

## POST /v1/search

The unified search endpoint. The gateway routes the query to the best data sources based on intent, then fuses and re-ranks the results. API key is optional — anonymous traffic is rate-limited per IP and consumes the daily free quota.

| Field | Type | Required | Description |
|---|---|---|---|
| `query` | string | yes | Search query |
| `max_results` | int | no | Number of results to return, e.g. 10. Defaults to 10. Range: 1–20 |
| `tag` | string | no | Sub-domain capability tag, a single value in the form `{domain}.{sub_domain}`, e.g. `code.doc` |
| `zone` | string | no | Region, one of `cn` or `intl` |
| `language` | string | no | Preferred language, e.g. `zh-CN` or `en` |
| `params` | object | no | Extended parameters passed through to the routed data source, e.g. `{"ticker": "AAPL"}` |
| `format` | string | no | Output format, one of `json` or `markdown` |

### Example

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

### Errors

See the full [Error Codes](./error-codes.md) reference for every status the gateway can return.

<!-- /widget -->

## Related

- [Response Format](./response-format.md) — What a success and error body look like
- [Tags & Params](./tags-and-params.md) — Full domain taxonomy for the `tag` and `params` fields
- [Authentication](../get-started/authentication.md) — Anonymous vs. authenticated access
