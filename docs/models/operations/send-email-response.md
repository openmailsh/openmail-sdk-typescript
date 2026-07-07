# SendEmailResponse

Email sent (or idempotent replay)

## Example Usage

```typescript
import { SendEmailResponse } from "@openmail/sdk/models/operations";

let value: SendEmailResponse = {};
```

## Fields

| Field                                                                      | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `messageId`                                                                | *string*                                                                   | :heavy_minus_sign:                                                         | N/A                                                                        |
| `threadId`                                                                 | *string*                                                                   | :heavy_minus_sign:                                                         | N/A                                                                        |
| `providerMessageId`                                                        | *string*                                                                   | :heavy_minus_sign:                                                         | N/A                                                                        |
| `status`                                                                   | [operations.SendEmailStatus](../../models/operations/send-email-status.md) | :heavy_minus_sign:                                                         | N/A                                                                        |
| `additionalProperties`                                                     | Record<string, *any*>                                                      | :heavy_minus_sign:                                                         | N/A                                                                        |