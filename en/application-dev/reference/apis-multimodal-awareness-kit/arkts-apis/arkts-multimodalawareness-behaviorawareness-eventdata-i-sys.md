# EventData (System API)

```TypeScript
export interface EventData
```

Event event data.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface EventData--><!--Device-behaviorAwareness-export interface EventData-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## attributes

```TypeScript
attributes?: TimeAttributes | LocationAttributes | SystemEventAttributes
```

Scenario Attributes.

**Type:** [TimeAttributes](arkts-multimodalawareness-behaviorawareness-timeattributes-i-sys.md) &#124; [LocationAttributes](arkts-multimodalawareness-behaviorawareness-locationattributes-i-sys.md) &#124; [SystemEventAttributes](arkts-multimodalawareness-behaviorawareness-systemeventattributes-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventData-attributes?: TimeAttributes | LocationAttributes | SystemEventAttributes--><!--Device-EventData-attributes?: TimeAttributes | LocationAttributes | SystemEventAttributes-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## eventId

```TypeScript
eventId: string
```

Event ID.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventData-eventId: string--><!--Device-EventData-eventId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## eventType

```TypeScript
eventType: EventType
```

Event type.

**Type:** [EventType](arkts-multimodalawareness-behaviorawareness-eventtype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventData-eventType: EventType--><!--Device-EventData-eventType: EventType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Event Name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventData-name: string--><!--Device-EventData-name: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## params

```TypeScript
params?: Record<string, string | number | boolean>
```

Additional Parameters. Default value: Default behavior without additional parameters.

**Type:** Record&lt;string, string &#124; number &#124; boolean&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventData-params?: Record<string, string | int | boolean>--><!--Device-EventData-params?: Record<string, string | int | boolean>-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp: number
```

Occurrence timestamp. Unit: milliseconds.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventData-timestamp: long--><!--Device-EventData-timestamp: long-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
