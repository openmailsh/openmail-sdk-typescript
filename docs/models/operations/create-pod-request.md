# CreatePodRequest

## Example Usage

```typescript
import { CreatePodRequest } from "@openmail/sdk/models/operations";

let value: CreatePodRequest = {};
```

## Fields

| Field                                                                                                                                                               | Type                                                                                                                                                                | Required                                                                                                                                                            | Description                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `clientId`                                                                                                                                                          | *string*                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                  | Your own stable identifier for this pod (e.g. your user/tenant ID). Must be unique within your account. Use it in place of the pod ID on any pod or inbox endpoint. |
| `name`                                                                                                                                                              | *string*                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                  | Human-readable label shown in the console.                                                                                                                          |