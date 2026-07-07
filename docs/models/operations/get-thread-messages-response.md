# GetThreadMessagesResponse

Thread with messages

## Example Usage

```typescript
import { GetThreadMessagesResponse } from "@openmail/sdk/models/operations";

let value: GetThreadMessagesResponse = {};
```

## Fields

| Field                                       | Type                                        | Required                                    | Description                                 |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| `threadId`                                  | *string*                                    | :heavy_minus_sign:                          | N/A                                         |
| `subject`                                   | *string*                                    | :heavy_minus_sign:                          | N/A                                         |
| `isRead`                                    | *boolean*                                   | :heavy_minus_sign:                          | Whether the thread has been marked as read  |
| `data`                                      | [models.Message](../../models/message.md)[] | :heavy_minus_sign:                          | N/A                                         |
| `additionalProperties`                      | Record<string, *any*>                       | :heavy_minus_sign:                          | N/A                                         |