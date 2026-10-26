# PerceptionEvent (System API)

```TypeScript
export interface PerceptionEvent<T = BehaviorAwarenessPayload>
```

Aware event data. Events generated after MSDP convergent awareness clustering are pushed to the service side.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface PerceptionEvent<T = BehaviorAwarenessPayload>--><!--Device-behaviorAwareness-export interface PerceptionEvent<T = BehaviorAwarenessPayload>-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## confidence

```TypeScript
confidence: number
```

Confidence.The value 0 indicates no confidence, and the value 100 indicates complete confidence. Unit: Percentage. The value must be an integer within [0,100].

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PerceptionEvent-confidence: int--><!--Device-PerceptionEvent-confidence: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## domain

```TypeScript
domain: PerceptionDomain
```

Perceived domain type.

**Type:** [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PerceptionEvent-domain: PerceptionDomain--><!--Device-PerceptionEvent-domain: PerceptionDomain-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## generateTime

```TypeScript
generateTime: number
```

Generate the timestamp. Unit: milliseconds.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PerceptionEvent-generateTime: long--><!--Device-PerceptionEvent-generateTime: long-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## payload

```TypeScript
payload: T
```

Domain-specific data.

**Type:** T

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PerceptionEvent-payload: T--><!--Device-PerceptionEvent-payload: T-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## perceptionEventId

```TypeScript
perceptionEventId: string
```

Unique ID of an awareness event.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PerceptionEvent-perceptionEventId: string--><!--Device-PerceptionEvent-perceptionEventId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
