# CapsuleStyleOptions

胶囊样式选项。继承自[ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md)和[CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)。

**继承/实现关系：** CapsuleStyleOptions extends [ScanEffectOptions](arkts-arkui-scaneffectoptions-i.md), [CommonProgressStyleOptions](arkts-arkui-commonprogressstyleoptions-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## borderColor

```TypeScript
borderColor?: ResourceColor
```

内描边颜色。默认值：API version 10：'#33006cde'API version 11及以上：'#33007dff'

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderRadius

```TypeScript
borderRadius?: LengthMetrics
```

Capsule进度条圆角半径（不支持百分比设置）。取值范围：[0, 组件高度/2]。默认值：组件高度 / 2。设置非法数值时，按照默认值处理。

**类型：** LengthMetrics

**默认值：** min(width, height) / 2

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Length
```

内描边宽度。默认值：1vp取值范围：大于等于0的数值，不支持百分比设置。超出取值范围或设置非法值时按默认值处理。

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

文本内容，应用可自定义。当需要在Capsule进度条上显示自定义文本时传入此参数；不传入时不显示文本内容（若需显示百分比文本，可设置showDefaultPercentage为true）。从API version 20开始，支持Resource类型。

**类型：** [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## font

```TypeScript
font?: Font
```

文本样式。默认值：文本大小（不支持百分比设置）：12fp其他文本参数跟随Text组件的主题值。

**类型：** Font

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

文本颜色。默认值：'#ff182431'

**类型：** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showDefaultPercentage

```TypeScript
showDefaultPercentage?: boolean
```

显示百分比文本的开关。开启后，进度条上显示当前进度的百分比。设置了content属性时该属性不生效。true：表示显示百分比文本；false：表示不显示百分比文本。默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
