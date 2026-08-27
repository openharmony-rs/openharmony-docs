# DialogOptions

设置弹框特有的属性以及提供给用户自定义的点击触发动作。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { InterstitialDialogAction, IconStyle, TitlePosition, BottomOffset } from '@kit.ArkUI';
```

## backgroundImage

```TypeScript
backgroundImage?: Resource
```

弹框背景图片。默认为纯色背景，颜色值为#EBEEF5。

**类型：** Resource

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottomOffsetType

```TypeScript
bottomOffsetType?: BottomOffset
```

弹框距离底部偏移类型，需根据是否存在菜单栏选择对应值。默认值为BottomOffset.OFFSET_FOR_NONE。

**类型：** [BottomOffset](arkts-arkui-atomicservice-interstitialdialogaction-bottomoffset-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## foregroundImage

```TypeScript
foregroundImage?: Resource
```

弹框前景图片。默认为空，即不显示前景图片。

**类型：** Resource

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iconStyle

```TypeScript
iconStyle?: IconStyle
```

关闭按钮图标的样式（亮调或者暗调）。默认值：IconStyle.LIGHT

**类型：** [IconStyle](arkts-arkui-atomicservice-interstitialdialogaction-iconstyle-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDialogClick

```TypeScript
onDialogClick?: Callback<void>
```

点击弹框任意位置后触发的用户自定义动作。默认调用closeDialog方法关闭弹框。 说明：点击关闭按钮区域时仅触发onDialogClose，不触发本回调；若需同时触发，请在onDialogClose中显式调用本回调逻辑。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDialogClose

```TypeScript
onDialogClose?: Callback<void>
```

点击关闭按钮后触发的用户自定义动作。默认调用closeDialog方法关闭弹框。

**类型：** Callback&lt;void&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitle

```TypeScript
subtitle?: ResourceStr
```

弹框副标题文本。默认为空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## subtitleColor

```TypeScript
subtitleColor?: ResourceStr | Color
```

弹框副标题文本颜色。默认为\$r('sys.color.ohos_id_color_text_secondary_contrary')。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md) \| Color

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

弹框主标题文本。默认为空字符串。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titleColor

```TypeScript
titleColor?: ResourceStr | Color
```

弹框主标题文本颜色。默认为\$r('sys.color.ohos_id_color_text_primary_contrary')。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md) \| Color

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## titlePosition

```TypeScript
titlePosition?: TitlePosition
```

主标题在弹框中的位置，在副标题的上方或者在副标题的下方。需设置subtitle属性后本参数才生效。默认值：TitlePosition.TOP

**类型：** [TitlePosition](arkts-arkui-atomicservice-interstitialdialogaction-titleposition-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## uiContext

```TypeScript
uiContext: UIContext
```

UI上下文实例。

**类型：** [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
