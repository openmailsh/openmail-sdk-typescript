# GetAttachmentTextResponse

Extracted text content

## Example Usage

```typescript
import { GetAttachmentTextResponse } from "@openmail/sdk/models/operations";

let value: GetAttachmentTextResponse = {};
```

## Fields

| Field                                             | Type                                              | Required                                          | Description                                       |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `filename`                                        | *string*                                          | :heavy_minus_sign:                                | N/A                                               |
| `contentType`                                     | *string*                                          | :heavy_minus_sign:                                | N/A                                               |
| `extractionMethod`                                | *string*                                          | :heavy_minus_sign:                                | Method used to extract text (e.g. pdf, docx, ocr) |
| `text`                                            | *string*                                          | :heavy_minus_sign:                                | N/A                                               |
| `additionalProperties`                            | Record<string, *any*>                             | :heavy_minus_sign:                                | N/A                                               |