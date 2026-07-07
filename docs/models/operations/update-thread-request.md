# UpdateThreadRequest

## Example Usage

```typescript
import { UpdateThreadRequest } from "@openmail/sdk/models/operations";

let value: UpdateThreadRequest = {
  id: "<id>",
  body: {
    isRead: true,
  },
};
```

## Fields

| Field                                                                                       | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `id`                                                                                        | *string*                                                                                    | :heavy_check_mark:                                                                          | N/A                                                                                         |
| `body`                                                                                      | [operations.UpdateThreadRequestBody](../../models/operations/update-thread-request-body.md) | :heavy_check_mark:                                                                          | N/A                                                                                         |