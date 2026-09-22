# getAllCapabilityList

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## getAllCapabilityList

```TypeScript
function getAllCapabilityList(): Promise<Capability[]>
```

Returns the list of all capabilities.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Capability](arkts-multimodalawareness-carawareness-capability-e.md)[]&gt; | Promise used to return the list of all capabilities. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Car awareness not supported. Function can not work correctly due to limited device capabilities. |
| [34000001](../errorcode-carAwareness.md#34000001-service-exception) | Service exception. |
