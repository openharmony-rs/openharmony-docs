# @ohos.multimodalAwareness.metadataBinding

The **metadataBinding** module provides metadata binding–specific functions such as metadata transfer, event subscription, and event unsubscription.

**Since:** 18

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
| [on](arkts-multimodalawareness-metadatabinding-on-f.md#onoperationsubmitmetadata) | Subscribes to a system event to obtain the encoded metadata. The application needs to register a callback to return the encoded metadata when the registered system event occurs. |
| [submitMetadata](arkts-multimodalawareness-metadatabinding-submitmetadata-f.md) | Transfers the metadata to be encoded to the MSDP. The MSDP determines whether to transfer the metadata to the system application or service that calls the encoding API. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [decodeImage](arkts-multimodalawareness-metadatabinding-decodeimage-f-sys.md) | Decodes the information carried in the image. This API uses a promise to return the result. |
| [encodeImage](arkts-multimodalawareness-metadatabinding-encodeimage-f-sys.md) | Encodes metadata into an image. This API uses a promise to return the result. |
| [notifyMetadataBindingEvent](arkts-multimodalawareness-metadatabinding-notifymetadatabindingevent-f-sys.md) | Transfers metadata to the application or service that calls the encoding API. This API uses a promise to return the result. |
<!--DelEnd-->
