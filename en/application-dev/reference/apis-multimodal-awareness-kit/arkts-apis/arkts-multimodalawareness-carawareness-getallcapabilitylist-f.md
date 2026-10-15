# getAllCapabilityList

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## getAllCapabilityList

```TypeScript
function getAllCapabilityList(): Promise<Capability[]>
```

Obtains the list of all car awareness capabilities supported by the current device.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-carAwareness-function getAllCapabilityList(): Promise<Capability[]>--><!--Device-carAwareness-function getAllCapabilityList(): Promise<Capability[]>-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Capability](arkts-multimodalawareness-carawareness-capability-e.md)[]&gt; | Promise used to return the list of awareness capability enums supported by the device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
