# TipsDialog

提示弹出框，用于提醒用户关注特定事项或进行确认操作。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-export declare struct TipsDialog--><!--Device-unnamed-export declare struct TipsDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkAction

```TypeScript
checkAction?: (isChecked: boolean) => void
```

checkbox的选中状态改变事件。isChecked为true时，表示checkbox已选中，isChecked为false时，表示checkbox未选中。现推荐使用onCheckedChange&lt;sup&gt;12+&lt;/sup&gt;。

**类型：** (isChecked: boolean) =&gt; void

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-checkAction?: (isChecked: boolean) => void--><!--Device-TipsDialog-checkAction?: (isChecked: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkTips

```TypeScript
checkTips?: ResourceStr
```

checkbox的提示内容。 默认不设置或设置为undefined，提示内容不显示。

**类型：** ResourceStr

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-checkTips?: ResourceStr--><!--Device-TipsDialog-checkTips?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

提示弹出框内容。 默认不设置或设置为undefined，弹出框内容不显示。

**类型：** ResourceStr

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-content?: ResourceStr--><!--Device-TipsDialog-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

提示弹出框控制器，用于控制弹出框的显示和隐藏。 **说明：** 未使用@Require装饰，构造时不强制校验参数。

**类型：** CustomDialogController

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-controller: CustomDialogController--><!--Device-TipsDialog-controller: CustomDialogController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageRes

```TypeScript
imageRes: ResourceStr | PixelMap
```

展示的图片。

**类型：** ResourceStr \| PixelMap

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-imageRes: ResourceStr | PixelMap--><!--Device-TipsDialog-imageRes: ResourceStr | PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: SizeOptions
```

自定义图片尺寸。 默认值：64*64vp

**类型：** SizeOptions

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-imageSize?: SizeOptions--><!--Device-TipsDialog-imageSize?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isChecked

```TypeScript
@Prop isChecked?: boolean
```

value为true时，表示checkbox已选中，value为false时，表示未选中。 默认值：false

**类型：** boolean

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-@Prop isChecked?: boolean--><!--Device-TipsDialog-@Prop isChecked?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
onCheckedChange?: Callback<boolean>
```

checkbox的选中状态改变事件回调。回调参数类型为boolean，true表示checkbox已选中，false表示checkbox未选中。

**类型：** [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;boolean&gt;

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-onCheckedChange?: Callback<boolean>--><!--Device-TipsDialog-onCheckedChange?: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: ButtonOptions
```

提示弹出框左侧按钮。 默认不设置或设置为undefined，左侧按钮不显示。

**类型：** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-primaryButton?: ButtonOptions--><!--Device-TipsDialog-primaryButton?: ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: ButtonOptions
```

提示弹出框右侧按钮。 默认不设置或设置为undefined，右侧按钮不显示。

**类型：** [ButtonOptions](arkts-arkui-arkui-advanced-dialog-buttonoptions-c.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-secondaryButton?: ButtonOptions--><!--Device-TipsDialog-secondaryButton?: ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: Theme | CustomTheme
```

主题信息，可以是CustomTheme或从onWillApplyTheme中获取的Theme实例。

**类型：** [Theme](arkts-arkui-arkui-theme-theme-i.md) \| [CustomTheme](arkts-arkui-arkui-theme-customtheme-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-theme?: Theme | CustomTheme--><!--Device-TipsDialog-theme?: Theme | CustomTheme-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## themeColorMode

```TypeScript
themeColorMode?: ThemeColorMode
```

自定义弹出框深浅色模式。 默认值：ThemeColorMode.SYSTEM

**类型：** ThemeColorMode

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-themeColorMode?: ThemeColorMode--><!--Device-TipsDialog-themeColorMode?: ThemeColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

提示弹出框标题。 默认不设置或设置为undefined，弹出框标题不显示。 **说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialog-title?: ResourceStr--><!--Device-TipsDialog-title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

