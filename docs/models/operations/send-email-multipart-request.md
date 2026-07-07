# SendEmailMultipartRequest

## Example Usage

```typescript
import { SendEmailMultipartRequest } from "@openmail/sdk/models/operations";

let value: SendEmailMultipartRequest = {
  id: "<id>",
  body: {
    to: "Brook.Lebsack@yahoo.com",
    body: "<value>",
  },
};
```

## Fields

| Field                                                                                                    | Type                                                                                                     | Required                                                                                                 | Description                                                                                              |
| -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| `id`                                                                                                     | *string*                                                                                                 | :heavy_check_mark:                                                                                       | N/A                                                                                                      |
| `idempotencyKey`                                                                                         | *string*                                                                                                 | :heavy_minus_sign:                                                                                       | Unique key for idempotent sends (e.g. UUID)                                                              |
| `body`                                                                                                   | [operations.SendEmailMultipartRequestBody](../../models/operations/send-email-multipart-request-body.md) | :heavy_check_mark:                                                                                       | N/A                                                                                                      |