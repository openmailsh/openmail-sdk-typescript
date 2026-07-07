# Attachments

## Overview

Downloading and extracting text from attachments

### Available Operations

* [getAttachment](#getattachment) - Get attachment
* [getAttachmentText](#getattachmenttext) - Extract attachment text

## getAttachment

Returns a 302 redirect to a signed URL for the attachment.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getAttachment" method="get" path="/v1/attachments/{messageId}/{filename}" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  await openmailSDK.attachments.getAttachment({
    messageId: "<id>",
    filename: "example.file",
  });


}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { attachmentsGetAttachment } from "@openmail/sdk/funcs/attachments-get-attachment.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await attachmentsGetAttachment(openmailSDK, {
    messageId: "<id>",
    filename: "example.file",
  });
  if (res.ok) {
    const { value: result } = res;
    
  } else {
    console.log("attachmentsGetAttachment failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetAttachmentRequest](../../models/operations/get-attachment-request.md)                                                                                           | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<void\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 404                            | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |

## getAttachmentText

Extracts and returns the plain text content of an attachment. Supports PDF, DOCX, XLSX, PPTX, images (via OCR), and other common formats. The result is cached on the message after the first extraction.

### Example Usage

<!-- UsageSnippet language="typescript" operationID="getAttachmentText" method="get" path="/v1/attachments/{messageId}/{filename}/text" -->
```typescript
import { OpenmailSDK } from "@openmail/sdk";

const openmailSDK = new OpenmailSDK({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const result = await openmailSDK.attachments.getAttachmentText({
    messageId: "<id>",
    filename: "example.file",
  });

  console.log(result);
}

run();
```

### Standalone function

The standalone function version of this method:

```typescript
import { OpenmailSDKCore } from "@openmail/sdk/core.js";
import { attachmentsGetAttachmentText } from "@openmail/sdk/funcs/attachments-get-attachment-text.js";

// Use `OpenmailSDKCore` for best tree-shaking performance.
// You can create one instance of it to use across an application.
const openmailSDK = new OpenmailSDKCore({
  bearerAuth: process.env["OPENMAILSDK_BEARER_AUTH"] ?? "",
});

async function run() {
  const res = await attachmentsGetAttachmentText(openmailSDK, {
    messageId: "<id>",
    filename: "example.file",
  });
  if (res.ok) {
    const { value: result } = res;
    console.log(result);
  } else {
    console.log("attachmentsGetAttachmentText failed:", res.error);
  }
}

run();
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `request`                                                                                                                                                                      | [operations.GetAttachmentTextRequest](../../models/operations/get-attachment-text-request.md)                                                                                  | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |
| `options`                                                                                                                                                                      | RequestOptions                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                             | Used to set various options for making HTTP requests.                                                                                                                          |
| `options.fetchOptions`                                                                                                                                                         | [RequestInit](https://developer.mozilla.org/en-US/docs/Web/API/Request/Request#options)                                                                                        | :heavy_minus_sign:                                                                                                                                                             | Options that are passed to the underlying HTTP request. This can be used to inject extra headers for examples. All `Request` options, except `method` and `body`, are allowed. |
| `options.retries`                                                                                                                                                              | [RetryConfig](../../lib/utils/retryconfig.md)                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                             | Enables retrying HTTP requests under certain failure conditions.                                                                                                               |

### Response

**Promise\<[operations.GetAttachmentTextResponse](../../models/operations/get-attachment-text-response.md)\>**

### Errors

| Error Type                     | Status Code                    | Content Type                   |
| ------------------------------ | ------------------------------ | ------------------------------ |
| errors.ErrorT                  | 404, 422                       | application/json               |
| errors.OpenmailSDKDefaultError | 4XX, 5XX                       | \*/\*                          |