# ListInboxesRequest

## Example Usage

```typescript
import { ListInboxesRequest } from "@openmail/sdk/models/operations";

let value: ListInboxesRequest = {};
```

## Fields

| Field                                                                                                                 | Type                                                                                                                  | Required                                                                                                              | Description                                                                                                           |
| --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                               | *number*                                                                                                              | :heavy_minus_sign:                                                                                                    | Max results to return (clamped to 100)                                                                                |
| `offset`                                                                                                              | *number*                                                                                                              | :heavy_minus_sign:                                                                                                    | Number of results to skip                                                                                             |
| `podId`                                                                                                               | *string*                                                                                                              | :heavy_minus_sign:                                                                                                    | Filter to inboxes in a single pod. Accepts the pod ID or your own `clientId`. An unknown value returns an empty list. |