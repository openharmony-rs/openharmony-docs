# PopupOptions

PopupOptions定义Popup的具体样式参数。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: [PopupButtonOptions?, PopupButtonOptions?]
```

设置popup操作按钮，按钮最多设置两个。

默认不显示按钮。

**类型：** [PopupButtonOptions?, PopupButtonOptions?]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。

默认值：Direction.Auto

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: PopupIconOptions
```

设置popup图标。

**说明：**

当width和height设置异常值或0时不显示。

默认不显示图标。

**类型：** PopupIconOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: Dimension
```

设置popup的最大宽度，通过此接口popup可以自定义宽度显示。

**说明：**

1. 在使用引用资源类型时，规定其参数类型要与属性方法本身类型一致。
2. maxWidth是数字类型，支持float和integer，例如`$r('app.float.maxWidth')`、`$r('app.integer.maxWidth')`。
3. 当类型为Resource时，如果未设置单位，默认单位为px。

默认值：400vp

**类型：** Dimension

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: PopupTextOptions
```

设置popup内容文本。

**说明：**

message不支持设置fontWeight。

默认不显示内容文本。

**类型：** PopupTextOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
onClose?: () => void
```

设置popup关闭按钮回调函数。

默认不设置关闭按钮回调函数。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

设置popup关闭按钮。

true：显示关闭按钮；false：不显示关闭按钮。

Resource：显示对应的图标。

默认值：true

**类型：** boolean | Resource

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: PopupTextOptions
```

设置popup标题文本。

默认不显示标题文本。

**类型：** PopupTextOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

