# ActionData (System API)

```TypeScript
export interface ActionData
```

Operation action data.

**Since:** 26.1.0

<!--Device-behaviorAwareness-export interface ActionData--><!--Device-behaviorAwareness-export interface ActionData-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## actionId

```TypeScript
actionId: string
```

Action ID (specific prefix format).

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionData-actionId: string--><!--Device-ActionData-actionId: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## actionType

```TypeScript
actionType: ActionType
```

Action Type.

**Type:** [ActionType](arkts-multimodalawareness-behaviorawareness-actiontype-e-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionData-actionType: ActionType--><!--Device-ActionData-actionType: ActionType-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## attributes

```TypeScript
attributes?: SystemActionAttributes
```

Scenario Attributes.

**Type:** [SystemActionAttributes](arkts-multimodalawareness-behaviorawareness-systemactionattributes-i-sys.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionData-attributes?: SystemActionAttributes--><!--Device-ActionData-attributes?: SystemActionAttributes-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Action Name.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionData-name: string--><!--Device-ActionData-name: string-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

## params

```TypeScript
params?: Record<string, string | number | boolean>
```

Additional Parameters. Default value: Default behavior: no additional parameters.

**Type:** Record&lt;string, string &#124; number &#124; boolean&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionData-params?: Record<string, string | int | boolean>--><!--Device-ActionData-params?: Record<string, string | int | boolean>-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.
