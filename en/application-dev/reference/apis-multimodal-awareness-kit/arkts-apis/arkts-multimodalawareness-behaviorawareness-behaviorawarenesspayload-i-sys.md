# BehaviorAwarenessPayload (System API)

```TypeScript
export interface BehaviorAwarenessPayload
```

Habit-aware domain payload. Specific data in the HABIT_Awareness domain.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface BehaviorAwarenessPayload--><!--Device-behaviorAwareness-export interface BehaviorAwarenessPayload-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## action

```TypeScript
action: ActionData[]
```

Associated Actions.

**Type:** [ActionData](arkts-multimodalawareness-behaviorawareness-actiondata-i-sys.md)[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BehaviorAwarenessPayload-action: ActionData[]--><!--Device-BehaviorAwarenessPayload-action: ActionData[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## patternType

```TypeScript
patternType: PatternType
```

Perception mode type.

**Type:** [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BehaviorAwarenessPayload-patternType: PatternType--><!--Device-BehaviorAwarenessPayload-patternType: PatternType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## triggerEvent

```TypeScript
triggerEvent: EventData[]
```

Triggering event.

**Type:** [EventData](arkts-multimodalawareness-behaviorawareness-eventdata-i-sys.md)[]

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-BehaviorAwarenessPayload-triggerEvent: EventData[]--><!--Device-BehaviorAwarenessPayload-triggerEvent: EventData[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
