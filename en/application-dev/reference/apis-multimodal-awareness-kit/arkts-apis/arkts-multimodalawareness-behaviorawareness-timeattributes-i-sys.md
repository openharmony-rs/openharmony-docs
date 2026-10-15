# TimeAttributes (System API)

```TypeScript
export interface TimeAttributes
```

Time-based scenario attributes.

**Since:** 26.2.0

<!--Device-behaviorAwareness-export interface TimeAttributes--><!--Device-behaviorAwareness-export interface TimeAttributes-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## dayOfMonth

```TypeScript
dayOfMonth?: number
```

Day of the month. Unit: day. The value must be an integer within [1,31]. Default value: The default value is 0.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimeAttributes-dayOfMonth?: int--><!--Device-TimeAttributes-dayOfMonth?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## dayOfWeek

```TypeScript
dayOfWeek?: number
```

Day of the week. The value must be an integer within [1,7]. Default value: The default value is 0.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimeAttributes-dayOfWeek?: int--><!--Device-TimeAttributes-dayOfWeek?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## kind

```TypeScript
kind: 'time'
```

Discriminator field, fixed as 'time'.

**Type:** 'time'

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimeAttributes-kind: 'time'--><!--Device-TimeAttributes-kind: 'time'-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## recurrence

```TypeScript
recurrence: RecurrenceType
```

Recurrence type.

**Type:** [RecurrenceType](arkts-multimodalawareness-behaviorawareness-recurrencetype-e-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimeAttributes-recurrence: RecurrenceType--><!--Device-TimeAttributes-recurrence: RecurrenceType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## timePoint

```TypeScript
timePoint: string
```

Time point (HH:mm format, e.g. "08:30").

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimeAttributes-timePoint: string--><!--Device-TimeAttributes-timePoint: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
