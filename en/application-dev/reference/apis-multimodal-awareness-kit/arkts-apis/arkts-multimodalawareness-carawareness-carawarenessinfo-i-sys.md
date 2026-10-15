# CarAwarenessInfo (System API)

```TypeScript
export interface CarAwarenessInfo
```

Interface for general car awareness response info.

**Since:** 26.0.1

<!--Device-carAwareness-export interface CarAwarenessInfo--><!--Device-carAwareness-export interface CarAwarenessInfo-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { carAwareness } from '@kit.MultimodalAwarenessKit';
```

## awarenessEvent

```TypeScript
awarenessEvent?:Record<string, Object>
```

Key-value pair of the awareness result data. Different capabilities return different fields.

**Type:** Record&lt;string, Object&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CarAwarenessInfo-awarenessEvent?:Record<string, Object>--><!--Device-CarAwarenessInfo-awarenessEvent?:Record<string, Object>-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

## capability

```TypeScript
capability: Capability
```

Indicates specific awareness capability type.

**Type:** [Capability](arkts-multimodalawareness-carawareness-capability-e.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CarAwarenessInfo-capability: Capability--><!--Device-CarAwarenessInfo-capability: Capability-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp: number
```

Timestamp of the recognition result. Unit: ms.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-CarAwarenessInfo-timestamp: number--><!--Device-CarAwarenessInfo-timestamp: number-End-->

**System capability:** SystemCapability.MultimodalAwareness.CarAwareness

**System API:** This is a system API.
