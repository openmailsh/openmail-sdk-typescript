<!-- Start SDK Example Usage [usage] -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.pods.createPod({});

  console.log(result);
}

run();

```
<!-- End SDK Example Usage [usage] -->