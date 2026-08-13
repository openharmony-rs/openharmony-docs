# PopupOptions

PopupOptions定义Popup的具体样式参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface PopupOptions--><!--Device-unnamed-export interface PopupOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttons

```TypeScript
buttons?: [
    PopupButtonOptions | undefined,
    PopupButtonOptions | undefined
  ]
```

设置popup操作按钮，按钮最多设置两个。 默认不显示按钮。

**类型：** [     PopupButtonOptions \| undefined,     PopupButtonOptions \| undefined   ]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-buttons?: [    PopupButtonOptions | undefined,    PopupButtonOptions | undefined  ]--><!--Device-PopupOptions-buttons?: [    PopupButtonOptions | undefined,    PopupButtonOptions | undefined  ]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。 默认值：Direction.Auto

**类型：** Direction

**默认值：** Direction.Auto

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-direction?: Direction--><!--Device-PopupOptions-direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: PopupIconOptions
```

设置popup图标。 **说明：** 当width和height设置异常值或0时不显示。 默认不显示图标。

**类型：** [PopupIconOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-popup-popupiconoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-icon?: PopupIconOptions--><!--Device-PopupOptions-icon?: PopupIconOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: Dimension
```

设置popup的最大宽度，通过此接口popup可以自定义宽度显示。 **说明：** 1. 在使用引用资源类型时，规定其参数类型要与属性方法本身类型一致。 2. maxWidth是数字类型，支持float和integer，例如`\$r('app.float.maxWidth')`、`\$r('app.integer.maxWidth')`。 3. 当类型为Resource时，如果未设置单位，默认单位为px。 默认值：400vp

**类型：** Dimension

**默认值：** 400.0_vp

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-maxWidth?: Dimension--><!--Device-PopupOptions-maxWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message?: PopupTextOptions
```

设置popup内容文本。 **说明：** message不支持设置fontWeight。 默认不显示内容文本。 **ArkTS模式：** 该接口仅适用于ArkTS-Sta。 **ArkTS-Sta起始版本：** 23

**类型：** [PopupTextOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-message?: PopupTextOptions--><!--Device-PopupOptions-message?: PopupTextOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onClose

```TypeScript
onClose?: VoidCallback
```

设置popup关闭按钮回调函数。

**类型：** VoidCallback

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-onClose?: VoidCallback--><!--Device-PopupOptions-onClose?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showClose

```TypeScript
showClose?: boolean | Resource
```

设置popup关闭按钮。 true：显示关闭按钮；false：不显示关闭按钮。 Resource：显示对应的图标。 默认值：true

**类型：** boolean \| Resource

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-showClose?: boolean | Resource--><!--Device-PopupOptions-showClose?: boolean | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: PopupTextOptions
```

设置popup标题文本。 默认不显示标题文本。

**类型：** [PopupTextOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-advanced-popup-popuptextoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PopupOptions-title?: PopupTextOptions--><!--Device-PopupOptions-title?: PopupTextOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

