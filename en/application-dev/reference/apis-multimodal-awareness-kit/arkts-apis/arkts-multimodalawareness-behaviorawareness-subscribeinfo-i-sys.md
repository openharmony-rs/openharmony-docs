# SubscribeInfo (System API)

```TypeScript
export interface SubscribeInfo
```

Subscription Options. Defines the filter criteria for subscriptions.

**Since:** 26.2.0

<!--Device-behaviorAwareness-export interface SubscribeInfo--><!--Device-behaviorAwareness-export interface SubscribeInfo-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## domain

```TypeScript
domain: PerceptionDomain
```

Perception domain type.

**Type:** [PerceptionDomain](arkts-multimodalawareness-behaviorawareness-perceptiondomain-e-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SubscribeInfo-domain: PerceptionDomain--><!--Device-SubscribeInfo-domain: PerceptionDomain-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## patternTypes

```TypeScript
patternTypes?: PatternType[]
```

Subtype Filtering (Optional. If this parameter is not specified, all modes in the domain are subscribed.). Default value: Subscribe to all subtypes in the domain without filtering.

**Type:** [PatternType](arkts-multimodalawareness-behaviorawareness-patterntype-e-sys.md)[]

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SubscribeInfo-patternTypes?: PatternType[]--><!--Device-SubscribeInfo-patternTypes?: PatternType[]-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
