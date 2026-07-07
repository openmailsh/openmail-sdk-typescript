# ListMessagesRequest

## Example Usage

```typescript
import { ListMessagesRequest } from "@openmail/sdk/models/operations";

let value: ListMessagesRequest = {
  id: "<id>",
};
```

## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `limit`                                                      | *number*                                                     | :heavy_minus_sign:                                           | N/A                                                          |
| `offset`                                                     | *number*                                                     | :heavy_minus_sign:                                           | N/A                                                          |
| `direction`                                                  | [models.MessageDirection](../../models/message-direction.md) | :heavy_minus_sign:                                           | N/A                                                          |
| `id`                                                         | *string*                                                     | :heavy_check_mark:                                           | N/A                                                          |