# SystemActionAttributes (System API)

```TypeScript
export interface SystemActionAttributes
```

System control scenario attributes.

**Since:** 26.2.0

<!--Device-behaviorAwareness-export interface SystemActionAttributes--><!--Device-behaviorAwareness-export interface SystemActionAttributes-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## adjustment

```TypeScript
adjustment?: AdjustmentDirection
```

Adjustment direction.

**Type:** [AdjustmentDirection](arkts-multimodalawareness-behaviorawareness-adjustmentdirection-e-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-adjustment?: AdjustmentDirection--><!--Device-SystemActionAttributes-adjustment?: AdjustmentDirection-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## appName

```TypeScript
appName?: string
```

Application name.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-appName?: string--><!--Device-SystemActionAttributes-appName?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## kind

```TypeScript
kind: 'systemAction'
```

Discriminator field, fixed as 'systemAction'.

**Type:** 'systemAction'

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-kind: 'systemAction'--><!--Device-SystemActionAttributes-kind: 'systemAction'-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## operation

```TypeScript
operation: Operation
```

Operation target (on/off/toggle).

**Type:** [Operation](arkts-multimodalawareness-behaviorawareness-operation-e-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-operation: Operation--><!--Device-SystemActionAttributes-operation: Operation-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## packageName

```TypeScript
packageName?: string
```

Application package name.

**Type:** string

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-packageName?: string--><!--Device-SystemActionAttributes-packageName?: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## soundMode

```TypeScript
soundMode?: SoundMode
```

Sound mode.

**Type:** [SoundMode](arkts-multimodalawareness-behaviorawareness-soundmode-e-sys.md)

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-soundMode?: SoundMode--><!--Device-SystemActionAttributes-soundMode?: SoundMode-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## value

```TypeScript
value?: number
```

Absolute value indicates the fixed value of the brightness or volume. Unit: Percentage. The value must be an integer within [0,100]. Default value: The default value is 0.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemActionAttributes-value?: int--><!--Device-SystemActionAttributes-value?: int-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
