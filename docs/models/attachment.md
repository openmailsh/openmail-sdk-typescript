# Attachment

## Example Usage

```typescript
import { Attachment } from "@openmail/sdk/models";

let value: Attachment = {};
```

## Fields

| Field                   | Type                    | Required                | Description             |
| ----------------------- | ----------------------- | ----------------------- | ----------------------- |
| `filename`              | *string*                | :heavy_minus_sign:      | N/A                     |
| `contentType`           | *string*                | :heavy_minus_sign:      | N/A                     |
| `sizeBytes`             | *number*                | :heavy_minus_sign:      | N/A                     |
| `url`                   | *string*                | :heavy_minus_sign:      | Signed URL for download |
| `additionalProperties`  | Record<string, *any*>   | :heavy_minus_sign:      | N/A                     |