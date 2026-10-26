# ActionData（系统接口）

```TypeScript
export interface ActionData
```

操作动作数据。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface ActionData--><!--Device-behaviorAwareness-export interface ActionData-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## actionId

```TypeScript
actionId: string
```

动作 ID（特定前缀格式）。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionData-actionId: string--><!--Device-ActionData-actionId: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## actionType

```TypeScript
actionType: ActionType
```

动作类型。

**类型：** [ActionType](arkts-multimodalawareness-behaviorawareness-actiontype-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionData-actionType: ActionType--><!--Device-ActionData-actionType: ActionType-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## attributes

```TypeScript
attributes?: SystemActionAttributes
```

场景属性。

**类型：** [SystemActionAttributes](arkts-multimodalawareness-behaviorawareness-systemactionattributes-i-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionData-attributes?: SystemActionAttributes--><!--Device-ActionData-attributes?: SystemActionAttributes-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

动作名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionData-name: string--><!--Device-ActionData-name: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## params

```TypeScript
params?: Record<string, string | number | boolean>
```

附加参数。默认值：无附加参数时的默认行为。

**类型：** Record&lt;string, string &#124; number &#124; boolean&gt;

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ActionData-params?: Record<string, string | int | boolean>--><!--Device-ActionData-params?: Record<string, string | int | boolean>-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
