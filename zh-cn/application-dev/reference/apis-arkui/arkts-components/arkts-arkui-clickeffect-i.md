# ClickEffect

定义点击效果。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## level

```TypeScript
level: ClickEffectLevel
```

设置当前组件的点击回弹效果。

默认值：ClickEffectLevel.LIGHT

**说明：**

当level为undefined或者null时， ClickEffect采用ClickEffectLevel.LIGHT对应的回弹效果，缩放比参照scale说明。

**类型：** ClickEffectLevel

**默认值：** ClickEffectLevel.LIGHT

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: number
```

回弹缩放比例，支持在设置ClickEffectLevel的基础上微调。

**说明：**

当level为ClickEffectLevel.LIGHT时，默认值：0.90

当level为ClickEffectLevel.MIDDLE或者ClickEffectLevel.HEAVY时，默认值：0.95

当level为undefined或者null时，level为ClickEffectLevel.LIGHT，默认值：0.90

当scale为undefined或者null时，使用当前level对应的默认缩放比例。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

