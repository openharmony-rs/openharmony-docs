# @ohos.multimodalAwareness.metadataBinding(Metadata binding–specific)

This module provides metadata binding capability invocation, including encoded content transfer, event subscription, and event unsubscription. Metadata binding allows system applications to obtain encoded content from third-party applications, supports real-time event listening and callback mechanisms, and is suitable for scenarios where a system application makes a request (such as a screenshot) and obtains application binding data, improving user experience through cross-application data transfer.

**Since:** 18

<!--Device-unnamed-declare namespace metadataBinding--><!--Device-unnamed-declare namespace metadataBinding-End-->

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [off](arkts-multimodalawareness-metadatabinding-off-f.md#offoperationsubmitmetadata) | Unsubscribes from system events that are used to obtain the encoded metadata. The respective callback will be unregistered. |
| [on](arkts-multimodalawareness-metadatabinding-on-f.md#onoperationsubmitmetadata) | Subscribes to the event of a system application requesting to obtain encoded content. This event is triggered when a system application (such as a screenshot) requests to obtain the encoded content of an application. After the application registers a callback, it is notified through the callback when the event occurs. After subscribing to the event by calling on(), the application must call off() to unsubscribe and release the listening resources when the event no longer needs to be listened for. |
| [submitMetadata](arkts-multimodalawareness-metadatabinding-submitmetadata-f.md) | A third-party application passes the content to be encoded to the API service, which then passes the content to the system application or service that invokes the encoding API. This API is called by third-party applications for system applications to subscribe to and obtain data. The system application must first subscribe to the event through the on('operationSubmitMetadata') method before it can receive the encoded content. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [decodeImage](arkts-multimodalawareness-metadatabinding-decodeimage-f-sys.md) | Decodes the information carried in the image. This API uses a promise to return the result. |
| [encodeImage](arkts-multimodalawareness-metadatabinding-encodeimage-f-sys.md) | Encodes metadata into an image. This API uses a promise to return the result. |
| [notifyMetadataBindingEvent](arkts-multimodalawareness-metadatabinding-notifymetadatabindingevent-f-sys.md) | Transfers metadata to the application or service that calls the encoding API. This API uses a promise to return the result. |
<!--DelEnd-->
