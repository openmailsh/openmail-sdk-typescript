# ListThreadsRequest

## Example Usage

```typescript
import { ListThreadsRequest } from "@openmail/sdk/models/operations";

let value: ListThreadsRequest = {
  id: "<id>",
};
```

## Fields

| Field                                                                                             | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `limit`                                                                                           | *number*                                                                                          | :heavy_minus_sign:                                                                                | N/A                                                                                               |
| `offset`                                                                                          | *number*                                                                                          | :heavy_minus_sign:                                                                                | N/A                                                                                               |
| `isRead`                                                                                          | [operations.IsRead](../../models/operations/is-read.md)                                           | :heavy_minus_sign:                                                                                | Filter by read status. true = read threads only, false = unread threads only. Omit to return all. |
| `id`                                                                                              | *string*                                                                                          | :heavy_check_mark:                                                                                | N/A                                                                                               |