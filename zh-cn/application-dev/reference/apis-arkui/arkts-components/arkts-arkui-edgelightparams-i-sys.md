# EdgeLightParams（系统接口）

定义边缘流光效果参数。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## color

```TypeScript
color?: ResourceColor
```

边缘流光颜色。

默认值：#FFFFFF，显示为白色。

**类型：** ResourceColor

**默认值：** #FFFFFF

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## intensity

```TypeScript
intensity?: number
```

边缘流光效果的发光强度。

取值范围：[0, 1]

默认值：1

**说明：**

值为0时，流光效果完全不可见。

值为1时，流光效果达到最大亮度。

设置大于1的值时，按值为1处理。

设置小于0的值时，按值为0处理。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## length

```TypeScript
length: Length
```

沿流动方向的边缘流光的投影长度（不支持百分比）。

取值范围：[0, +∞)

单位：vp

**说明：**

设置小于0的值时，按值为0处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: EdgeLightPosition
```

边缘流光位置。

**类型：** EdgeLightPosition

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## thickness

```TypeScript
thickness?: Length
```

边缘流光线条粗细（不支持百分比）。

取值范围：[0, +∞)

单位：vp

默认值：0

**说明：**

设置小于0的值时，按值为0处理。

**类型：** Length

**默认值：** 0vp

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

