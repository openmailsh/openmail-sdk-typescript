# SendEmailRequest

## Example Usage

```typescript
import { SendEmailRequest } from "@openmail/sdk/models/operations";

let value: SendEmailRequest = {
  id: "<id>",
  body: {
    to: "Rosalinda69@yahoo.com",
    body: "<value>",
  },
};
```

## Fields

| Field                                                                                 | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `id`                                                                                  | *string*                                                                              | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `idempotencyKey`                                                                      | *string*                                                                              | :heavy_minus_sign:                                                                    | Unique key for idempotent sends (e.g. UUID)                                           |
| `body`                                                                                | [operations.SendEmailRequestBody](../../models/operations/send-email-request-body.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |