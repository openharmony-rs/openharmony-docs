# CrownEvent

组件接收表冠事件的数据结构。内容包括时间戳、旋转角速度、旋转角度、表冠动作和阻止事件冒泡。

**起始版本：** 18

<!--Device-unnamed-declare interface CrownEvent--><!--Device-unnamed-declare interface CrownEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action: CrownAction
```

表冠动作。

**类型：** CrownAction

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CrownEvent-action: CrownAction--><!--Device-CrownEvent-action: CrownAction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angularVelocity

```TypeScript
angularVelocity: number
```

旋转角速度。

单位：deg/s

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CrownEvent-angularVelocity: number--><!--Device-CrownEvent-angularVelocity: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## degree

```TypeScript
degree: number
```

相对旋转角度。

单位：deg

取值范围:[-360, 360]。

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CrownEvent-degree: number--><!--Device-CrownEvent-degree: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopPropagation

```TypeScript
stopPropagation: Callback<void>
```

阻止[事件冒泡](docroot://ui/arkts-interaction-basic-principles.md#事件冒泡)。

**类型：** Callback&lt;void&gt;

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CrownEvent-stopPropagation: Callback<void>--><!--Device-CrownEvent-stopPropagation: Callback<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

时间戳。触发事件时距离系统启动的时间间隔。

单位：ns

**类型：** number

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CrownEvent-timestamp: number--><!--Device-CrownEvent-timestamp: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

