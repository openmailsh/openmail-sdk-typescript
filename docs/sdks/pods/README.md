# Pods

## Overview

Isolated sub-accounts for your end users or tenants

### Available Operations

* [createPod](#createpod) - Create pod
* [listPods](#listpods) - List pods
* [getPod](#getpod) - Get pod
* [updatePod](#updatepod) - Update pod
* [deletePod](#deletepod) - Delete pod

## createPod

Create a new pod (an isolated sub-account for one of your end users or tenants). Pass your own `clientId` to map the pod to a record in your system and address it later without storing the OpenMail ID.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="createPod" method="post" path="/v1/pods" -->
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

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { podsCreatePod } from "@openmail/sdk/funcs/pods-create-pod.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await podsCreatePod(openmailSDK, {});
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("podsCreatePod failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.CreatePodRequest](../../models/operations/create-pod-request.md)                                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Pod](../../models/pod.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 409                            | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## listPods

List all pods for your account. The default pod is always returned first. Supports pagination.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="listPods" method="get" path="/v1/pods" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.pods.listPods({});

  for await (const page of result) {
    console.log(page);
  }
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { podsListPods } from "@openmail/sdk/funcs/pods-list-pods.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await podsListPods(openmailSDK, {});
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("podsListPods failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListPodsRequest](../../models/operations/list-pods-request.md)                                                                                                     | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.ListPodsResponse](../../models/operations/list-pods-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 401                            | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## getPod

Retrieve a single pod by its OpenMail ID or your own `clientId`.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getPod" method="get" path="/v1/pods/{id}" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.pods.getPod({
    id: "<id>",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { podsGetPod } from "@openmail/sdk/funcs/pods-get-pod.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await podsGetPod(openmailSDK, {
    id: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("podsGetPod failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetPodRequest](../../models/operations/get-pod-request.md)                                                                                                         | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Pod](../../models/pod.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 404                            | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## updatePod

Update a pod's `clientId` or `name`. Only the fields you include are changed.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="updatePod" method="patch" path="/v1/pods/{id}" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.pods.updatePod({
    id: "<id>",
    body: {},
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { podsUpdatePod } from "@openmail/sdk/funcs/pods-update-pod.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await podsUpdatePod(openmailSDK, {
    id: "<id>",
    body: {},
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("podsUpdatePod failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UpdatePodRequest](../../models/operations/update-pod-request.md)                                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[models.Pod](../../models/pod.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 404, 409                       | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## deletePod

Permanently delete a pod. The pod must be empty (no inboxes or pod-scoped domains) and cannot be the default pod.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="deletePod" method="delete" path="/v1/pods/{id}" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  await openmailSDK.pods.deletePod({
    id: "<id>",
  });


}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { podsDeletePod } from "@openmail/sdk/funcs/pods-delete-pod.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await podsDeletePod(openmailSDK, {
    id: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    
  } else {
    console.log("podsDeletePod failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.DeletePodRequest](../../models/operations/delete-pod-request.md)                                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<void\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 404, 409                       | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |