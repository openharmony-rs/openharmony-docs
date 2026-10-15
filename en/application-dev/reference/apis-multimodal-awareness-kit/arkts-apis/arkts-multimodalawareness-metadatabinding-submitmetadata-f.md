# submitMetadata

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## submitMetadata

```TypeScript
function submitMetadata(metadata: string): void
```

A third-party application passes the content to be encoded to the API service, which then passes the content to the system application or service that invokes the encoding API. This API is called by third-party applications for system applications to subscribe to and obtain data. The system application must first subscribe to the event through the on('operationSubmitMetadata') method before it can receive the encoded content.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-metadataBinding-function submitMetadata(metadata: string): void--><!--Device-metadataBinding-function submitMetadata(metadata: string): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadata | string | Yes | Content to be encoded. The string length does not exceed 128 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32100001](../errorcode-metadataBinding.md#32100001-file-creation-failed) | Internal handling failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';

let metadata: string = 'sample metadata';
try {
  metadataBinding.submitMetadata(metadata);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to submit metadata. Code: ${err.code}, message: ${err.message}`);
}
```
