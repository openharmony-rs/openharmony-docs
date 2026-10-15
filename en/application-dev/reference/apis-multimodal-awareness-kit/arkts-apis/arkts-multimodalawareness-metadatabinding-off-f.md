# off

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## off('operationSubmitMetadata')

```TypeScript
function off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback<number>): void
```

Unsubscribes from system events that are used to obtain the encoded metadata. The respective callback will be unregistered.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-metadataBinding-function off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback<int>): void--><!--Device-metadataBinding-function off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback<int>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'operationSubmitMetadata' | Yes | Event type. This parameter has a fixed value of **operationSubmitMetadata**, indicating the system application's attempt to obtain the encoded metadata. |
| bundleName | string | Yes | Application bundle name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the encoded metadata. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32100001](../errorcode-metadataBinding.md#32100001-file-creation-failed) | Internal handling failed. |
| [32100005](../errorcode-metadataBinding.md#32100005-unsubscription-failed) | Unsubscribe Failed. Possible causes:<br> 1. Abnormal system capability. <br> 2. IPC communication abnormality. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';

let bundleName: string = 'com.example.app';
try {
  metadataBinding.off('operationSubmitMetadata', bundleName);
} catch (error) {
 const err = error as BusinessError;
 console.error(`Failed to unsubscribe operationSubmitMetadata event. Code: ${err.code}, message: ${err.message}`);
}
```
