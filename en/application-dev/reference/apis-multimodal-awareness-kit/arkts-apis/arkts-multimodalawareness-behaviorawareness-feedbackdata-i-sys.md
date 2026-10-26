# FeedbackData (System API)

```TypeScript
export interface FeedbackData
```

Feedback data.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface FeedbackData--><!--Device-behaviorAwareness-export interface FeedbackData-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## feedbackTime

```TypeScript
feedbackTime: number
```

Feedback timestamp . Unit: milliseconds.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FeedbackData-feedbackTime: long--><!--Device-FeedbackData-feedbackTime: long-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## feedbackType

```TypeScript
feedbackType: FeedbackType
```

Feedback Type.

**Type:** [FeedbackType](arkts-multimodalawareness-behaviorawareness-feedbacktype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FeedbackData-feedbackType: FeedbackType--><!--Device-FeedbackData-feedbackType: FeedbackType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## perceptionEventId

```TypeScript
perceptionEventId: string
```

Awareness event ID.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FeedbackData-perceptionEventId: string--><!--Device-FeedbackData-perceptionEventId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
