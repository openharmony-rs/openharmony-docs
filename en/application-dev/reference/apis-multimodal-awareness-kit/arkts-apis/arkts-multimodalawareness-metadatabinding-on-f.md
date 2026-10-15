# on

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## on('operationSubmitMetadata')

```TypeScript
function on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback<number>): void
```

Subscribes to the event of a system application requesting to obtain encoded content. This event is triggered when a system application (such as a screenshot) requests to obtain the encoded content of an application. After the application registers a callback, it is notified through the callback when the event occurs. After subscribing to the event by calling on(), the application must call off() to unsubscribe and release the listening resources when the event no longer needs to be listened for.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-metadataBinding-function on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback<int>): void--><!--Device-metadataBinding-function on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback<int>): void-End-->

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'operationSubmitMetadata' | Yes | Event type. This parameter has a fixed value of **operationSubmitMetadata**, indicating the system application's attempt to obtain the encoded metadata. |
| bundleName | string | Yes | Application bundle name. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the encoded metadata. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [32100001](../errorcode-metadataBinding.md#32100001-file-creation-failed) | Internal handling failed. |
| [32100004](../errorcode-metadataBinding.md#32100004-subscription-failed) | Subscribe Failed. Possible causes:<br>1. Abnormal system capability. <br>2. IPC communication abnormality. <br>3. Algorithm loading exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';

let bundleName: string = 'com.example.app';
try {
  metadataBinding.on('operationSubmitMetadata', bundleName, (event: number) => {
    if (event == 1) {
      console.info('The screenshot request is received and the app link is obtained');
    }
  });
} catch (error) {
  const err = error as BusinessError;
  console.error(`Failed to register operationSubmitMetadata event. Code: ${err.code}, message: ${err.message}`);
}
```
