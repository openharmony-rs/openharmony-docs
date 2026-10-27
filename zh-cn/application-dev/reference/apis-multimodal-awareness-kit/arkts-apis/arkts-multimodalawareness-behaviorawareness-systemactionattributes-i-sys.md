# SystemActionAttributes（系统接口）

```TypeScript
export interface SystemActionAttributes
```

系统控制类场景属性。

**起始版本：** 26.1.0

<!--Device-behaviorAwareness-export interface SystemActionAttributes--><!--Device-behaviorAwareness-export interface SystemActionAttributes-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## adjustment

```TypeScript
adjustment?: AdjustmentDirection
```

调节方向。

**类型：** [AdjustmentDirection](arkts-multimodalawareness-behaviorawareness-adjustmentdirection-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-adjustment?: AdjustmentDirection--><!--Device-SystemActionAttributes-adjustment?: AdjustmentDirection-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## appName

```TypeScript
appName?: string
```

应用名称。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-appName?: string--><!--Device-SystemActionAttributes-appName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## kind

```TypeScript
kind: 'systemAction'
```

判别字段，固定为 'systemAction'。

**类型：** 'systemAction'

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-kind: 'systemAction'--><!--Device-SystemActionAttributes-kind: 'systemAction'-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## operation

```TypeScript
operation: Operation
```

操作目标（开启/关闭/切换）。

**类型：** [Operation](arkts-multimodalawareness-behaviorawareness-operation-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-operation: Operation--><!--Device-SystemActionAttributes-operation: Operation-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## packageName

```TypeScript
packageName?: string
```

应用包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-packageName?: string--><!--Device-SystemActionAttributes-packageName?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## soundMode

```TypeScript
soundMode?: SoundMode
```

声音模式。

**类型：** [SoundMode](arkts-multimodalawareness-behaviorawareness-soundmode-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-soundMode?: SoundMode--><!--Device-SystemActionAttributes-soundMode?: SoundMode-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。

## value

```TypeScript
value?: number
```

绝对值，表示亮度或音量的固定值。单位：百分比。取值需为 [0,100] 范围内的整数。默认值：默认值为 0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemActionAttributes-value?: int--><!--Device-SystemActionAttributes-value?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.DeviceStatus

**系统接口：** 此接口为系统接口。
