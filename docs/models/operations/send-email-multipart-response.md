# SendEmailMultipartResponse

Email sent (or idempotent replay)

## Example Usage

```typescript
import { SendEmailMultipartResponse } from "@openmail/sdk/models/operations";

let value: SendEmailMultipartResponse = {};
```

## Fields

| Field                                                                                         | Type                                                                                          | Required                                                                                      | Description                                                                                   |
| --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| `messageId`                                                                                   | *string*                                                                                      | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `threadId`                                                                                    | *string*                                                                                      | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `providerMessageId`                                                                           | *string*                                                                                      | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `status`                                                                                      | [operations.SendEmailMultipartStatus](../../models/operations/send-email-multipart-status.md) | :heavy_minus_sign:                                                                            | N/A                                                                                           |
| `additionalProperties`                                                                        | Record<string, *any*>                                                                         | :heavy_minus_sign:                                                                            | N/A                                                                                           |