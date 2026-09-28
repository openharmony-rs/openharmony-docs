# @ohos.multimodalAwareness.metadataBinding (Metadata Binding)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: Msdp-->
<!--Owner: @codexu62-->
<!--Designer: @yuxiaoyang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=2216975af6485dc85c0ac70af19ecc4dbc873a78 translatedAt=2026-09-14T01:58:38.822Z pushedAt=2026-09-14T10:03:33.575Z -->

This module provides metadata binding capability invocation, including encoded content transfer, event subscription, and event unsubscription. Metadata binding allows system applications to obtain encoded content from third-party applications, supports real-time event listening and callback mechanisms, and is suitable for scenarios where a system application makes a request (such as a screenshot) and obtains application binding data, improving user experience through cross-application data transfer.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import
```ts
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## metadataBinding.submitMetadata
submitMetadata(metadata: string): void

A third-party application passes the content to be encoded to the API service, which then passes the content to the system application or service that invokes the encoding API. This API is called by third-party applications for system applications to subscribe to and obtain data. The system application must first subscribe to the event through the **on('operationSubmitMetadata')** method before it can receive the encoded content.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.MultimodalAwareness.MetadataBinding

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| metadata     | string                           | Yes   | Content to be encoded. The string length does not exceed 128 bytes. |

**Error codes** 

For details about the error codes, see [Metadata Binding Error Codes](errorcode-metadataBinding.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 32100001 | Internal handling failed. |

**Example**

```ts
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

## metadataBinding.on('operationSubmitMetadata')
on(type: 'operationSubmitMetadata', bundleName: string, callback: Callback&lt;number&gt;): void 

Subscribes to the event of a system application requesting to obtain encoded content. This event is triggered when a system application (such as a screenshot) requests to obtain the encoded content of an application. After the application registers a callback, it is notified through the callback when the event occurs. After subscribing to the event by calling **on()**, the application must call **off()** to unsubscribe and release the listening resources when the event no longer needs to be listened for.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.MultimodalAwareness.MetadataBinding 

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
|type|string|Yes|Event type. The value is fixed to **'operationSubmitMetadata'**, indicating that the system application obtains the encoded content.|
|bundleName|string|Yes|Application bundle name, used to identify the third-party application that registers the subscription event. When the event occurs, the system identifies and notifies the corresponding registered application by this bundle name. Ensure that the passed bundle name is a valid application bundle name.|
|callback|Callback&lt;number&gt;|Yes|Callback function, used to return the event code. When the event value is **1**, it indicates a screenshot event. Currently, only the screenshot event is supported. Value range: **1** (screenshot event). Note: The callback function should execute quickly to avoid blocking the UI thread.|

**Error codes**

For details about the error codes, see [Metadata Binding Error Codes](errorcode-metadataBinding.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 32100001 | Internal handling failed. |
| 32100004 | Subscribe Failed. Possible causes: 1. Abnormal system capability. 2. IPC communication abnormality. 3. Algorithm loading exception. |

**Example** 
```ts
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


## metadataBinding.off('operationSubmitMetadata')
off(type: 'operationSubmitMetadata', bundleName: string, callback?: Callback&lt;number&gt;): void

Unsubscribes from the event of the system obtaining encoded content. The **on('operationSubmitMetadata')** method must be called first to subscribe to the event. Calling this API without a subscription has no effect. After unsubscribing, the application will no longer receive encoded content transfer events.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.MultimodalAwareness.MetadataBinding 

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
|type|string|Yes| Event type. The value is fixed at **'operationSubmitMetadata'**, indicating that the system application obtains the encoding content.             |
|bundleName|string|Yes| Application bundle name, which identifies the bundle name of the registered application. It must be the same as the bundle name passed in during subscription.|
|callback|Callback&lt;number&gt;|No| Callback function used to return the event code. The callback function to be unsubscribed must be the same as the one passed in during subscription. It is recommended that you save the callback function reference during subscription and use the same reference when unsubscribing. If this parameter is not specified, all callback functions currently listening for this event are unsubscribed. |

**Error codes** 

For details about the error codes, see [Metadata Binding Error Codes](errorcode-metadataBinding.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 32100001 | Internal handling failed. |
| 32100005 | Unsubscribe Failed. Possible causes: 1. Abnormal system capability. 2. IPC communication abnormality. |

**Example**

```ts
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