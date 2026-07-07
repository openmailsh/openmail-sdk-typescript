# Messages

## Overview

Sending and listing messages

### Available Operations

* [sendEmail](#sendemail) - Send email
* [sendEmailMultipart](#sendemailmultipart) - Send email
* [listMessages](#listmessages) - List messages

## sendEmail

Send an email from an inbox. Requires Idempotency-Key header. Use threadId to reply to an existing thread. When replying on a thread where your inbox was CC'd (deliveryRole cc), the original sender is automatically CC'd.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="sendEmail" method="post" path="/v1/inboxes/{id}/send" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.messages.sendEmail({
    id: "<id>",
    body: {
      to: "Carson_Hickle-Barrows@gmail.com",
      body: "<value>",
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
import { messagesSendEmail } from "@openmail/sdk/funcs/messages-send-email.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await messagesSendEmail(openmailSDK, {
    id: "<id>",
    body: {
      to: "Carson_Hickle-Barrows@gmail.com",
      body: "<value>",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("messagesSendEmail failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.SendEmailRequest](../../models/operations/send-email-request.md)                                                                                                   | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.SendEmailResponse](../../models/operations/send-email-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 400, 402, 403, 404, 422, 429   | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## sendEmailMultipart

Send an email from an inbox. Requires Idempotency-Key header. Use threadId to reply to an existing thread. When replying on a thread where your inbox was CC'd (deliveryRole cc), the original sender is automatically CC'd.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="sendEmail_multipart" method="post" path="/v1/inboxes/{id}/send" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.messages.sendEmailMultipart({
    id: "<id>",
    body: {
      to: "Carson_Hickle-Barrows@gmail.com",
      body: "<value>",
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
import { messagesSendEmailMultipart } from "@openmail/sdk/funcs/messages-send-email-multipart.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await messagesSendEmailMultipart(openmailSDK, {
    id: "<id>",
    body: {
      to: "Carson_Hickle-Barrows@gmail.com",
      body: "<value>",
    },
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("messagesSendEmailMultipart failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.SendEmailMultipartRequest](../../models/operations/send-email-multipart-request.md)                                                                                | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.SendEmailMultipartResponse](../../models/operations/send-email-multipart-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 400, 402, 403, 404, 422, 429   | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## listMessages

List all messages in an inbox, across every thread. Supports pagination for high-volume inboxes.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="listMessages" method="get" path="/v1/inboxes/{id}/messages" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.messages.listMessages({
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
import { messagesListMessages } from "@openmail/sdk/funcs/messages-list-messages.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await messagesListMessages(openmailSDK, {
    id: "<id>",
  });
  if (res.ok) {
    const { value: result } = res;
    for await (const page of result) {
    console.log(page);
  }
  } else {
    console.log("messagesListMessages failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.ListMessagesRequest](../../models/operations/list-messages-request.md)                                                                                             | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.ListMessagesResponse](../../models/operations/list-messages-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 401, 404                       | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |