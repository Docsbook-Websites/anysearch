---
title: Response Format — AnySearch Search Results
description: The JSON shape of a successful AnySearch search response, its result and metadata fields, and the error body format.
---

# Response Format

A successful `200` response returns a JSON body with a `results` array and a `metadata` object.

## Result fields

| Field | Description |
|---|---|
| `title` (string) | Result title |
| `url` (string) | Original source URL |
| `snippet` (string) | Short summary |
| `content` (string) | Cleaned-up body content |

## Metadata fields

| Field | Description |
|---|---|
| `total_results` (int) | Total number of results returned |
| `search_time_ms` (int) | End-to-end search latency in milliseconds |

## Full response example

```json
{
  "code": 0,
  "message": "success",
  "request_id": "a035db5c-2380-4c1d-900d-15c3d1f41a5a",
  "data": {
    "results": [
      {
        "title": "Go 1.26 Release Notes",
        "url": "https://go.dev/doc/go1.26",
        "snippet": "Go 1.26 is a major release...",
        "content": "Detailed content here..."
      }
    ],
    "metadata": {
      "total_results": 10,
      "search_time_ms": 946
    }
  }
}
```

## Error response example

```json
{
  "code": -1,
  "message": "Missing required params for tag 'code.doc': library.",
  "request_id": "a035db5c-2380-4c1d-900d-15c3d1f41a5a"
}
```

## Related

- [Error Codes](./error-codes.md) — Every status code and symbol the gateway can return
- [Endpoints](./endpoints.md) — The request side of this same call
