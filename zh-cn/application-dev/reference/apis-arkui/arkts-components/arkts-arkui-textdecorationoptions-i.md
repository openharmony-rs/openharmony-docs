# TextDecorationOptions

文本装饰线的配置项。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

设置文本装饰线颜色。<br>默认值：Color.Black。

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: TextDecorationStyle
```

设置文本装饰线样式。<br>默认值：TextDecorationStyle.SOLID。

**类型：** [TextDecorationStyle](../arkts-apis/arkts-arkui-textdecorationstyle-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thicknessScale

```TypeScript
thicknessScale?: number
```

设置文本装饰线的粗细缩放比例。<br>默认值：1.0 <br>取值范围：[0, +∞) <br>**说明：** 负值按默认值处理。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TextDecorationType
```

设置文本装饰线类型。

**类型：** [TextDecorationType](../arkts-apis/arkts-arkui-textdecorationtype-e.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
