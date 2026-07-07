# UpdatePodRequest

## Example Usage

```typescript
import { UpdatePodRequest } from "@openmail/sdk/models/operations";

let value: UpdatePodRequest = {
  id: "<id>",
  body: {},
};
```

## Fields

| Field                                                                                 | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `id`                                                                                  | *string*                                                                              | :heavy_check_mark:                                                                    | Pod ID or your own `clientId`                                                         |
| `body`                                                                                | [operations.UpdatePodRequestBody](../../models/operations/update-pod-request-body.md) | :heavy_check_mark:                                                                    | N/A                                                                                   |