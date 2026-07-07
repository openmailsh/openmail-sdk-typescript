# Threads

## Overview

Conversation threads and read status

### Available Operations

* [listThreads](#listthreads) - List threads
* [getThreadMessages](#getthreadmessages) - Get thread messages
* [updateThread](#updatethread) - Update thread

## listThreads

List threads for an inbox. Use is_read to filter by read status — for example, ?is_read=false returns only unread threads.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="listThreads" method="get" path="/v1/inboxes/{id}/threads" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.threads.listThreads({
    id: "<id>",
  });

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
import { threadsListThreads } from "@openmail/sdk/funcs/threads-list-threads.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await threadsListThreads(openmailSDK, {
    id: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("threadsListThreads failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListThreadsRequest](../../models/operations/list-threads-request.md)                                                                                               | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.ListThreadsResponse](../../models/operations/list-threads-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 401, 404                       | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## getThreadMessages

Retrieve a thread and all of its messages in order, with read status and full message content.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getThreadMessages" method="get" path="/v1/threads/{id}/messages" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.threads.getThreadMessages({
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
import { threadsGetThreadMessages } from "@openmail/sdk/funcs/threads-get-thread-messages.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await threadsGetThreadMessages(openmailSDK, {
    id: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("threadsGetThreadMessages failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetThreadMessagesRequest](../../models/operations/get-thread-messages-request.md)                                                                                  | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetThreadMessagesResponse](../../models/operations/get-thread-messages-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 401, 404                       | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## updateThread

Update a thread's read status. Use this to mark a thread as read after your agent has processed it, or as unread to re-queue it for later processing.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="updateThread" method="patch" path="/v1/threads/{id}" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.threads.updateThread({
    id: "<id>",
    body: {
      isRead: false,
    },
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { threadsUpdateThread } from "@openmail/sdk/funcs/threads-update-thread.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await threadsUpdateThread(openmailSDK, {
    id: "<id>",
    body: {
      isRead: false,
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("threadsUpdateThread failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.UpdateThreadRequest](../../models/operations/update-thread-request.md)                                                                                             | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.UpdateThreadResponse](../../models/operations/update-thread-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 404                            | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |