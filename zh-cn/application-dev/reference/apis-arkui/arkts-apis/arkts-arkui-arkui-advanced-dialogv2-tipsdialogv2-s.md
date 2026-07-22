# TipsDialogV2

提示弹出框，即为带图形确认弹出框，必要时可通过图形化方式展现确认弹出框。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct TipsDialogV2--><!--Device-unnamed-export declare struct TipsDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## checkTips

```TypeScript
checkTips?: ResourceStr
```

选择框的提示内容。

默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-checkTips?: ResourceStr--><!--Device-TipsDialogV2-checkTips?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked?: boolean
```

checked为true时，表示选择框已选中。checked为false时，表示选择框未选中。

默认值：false

**类型：** boolean

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-checked?: boolean--><!--Device-TipsDialogV2-checked?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

提示弹出框内容。

默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-content?: ResourceStr--><!--Device-TipsDialogV2-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageBorderColor

```TypeScript
imageBorderColor?: ColorMetrics
```

图片描边颜色。

默认值：Color.Black

**类型：** ColorMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-imageBorderColor?: ColorMetrics--><!--Device-TipsDialogV2-imageBorderColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageBorderWidth

```TypeScript
imageBorderWidth?: LengthMetrics
```

图片描边宽度。

默认无描边效果。

**类型：** LengthMetrics

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-imageBorderWidth?: LengthMetrics--><!--Device-TipsDialogV2-imageBorderWidth?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageRes

```TypeScript
imageRes: ResourceStr | PixelMap
```

展示的图片。

**类型：** ResourceStr \| PixelMap

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-imageRes: ResourceStr | PixelMap--><!--Device-TipsDialogV2-imageRes: ResourceStr | PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
imageSize?: SizeOptions
```

自定义图片尺寸。

默认值：64*64vp

**类型：** SizeOptions

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-imageSize?: SizeOptions--><!--Device-TipsDialogV2-imageSize?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
onCheckedChange?: AdvancedDialogV2OnCheckedChange
```

选择框的选中状态改变事件。

默认无事件。

**类型：** AdvancedDialogV2OnCheckedChange

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange--><!--Device-TipsDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: AdvancedDialogV2Button
```

提示弹出框左侧按钮。

默认不显示。

**类型：** AdvancedDialogV2Button

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-primaryButton?: AdvancedDialogV2Button--><!--Device-TipsDialogV2-primaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: AdvancedDialogV2Button
```

提示弹出框右侧按钮。

默认不显示。

**类型：** AdvancedDialogV2Button

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-secondaryButton?: AdvancedDialogV2Button--><!--Device-TipsDialogV2-secondaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: ResourceStr
```

提示弹出框标题。

默认不显示。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-title?: ResourceStr--><!--Device-TipsDialogV2-title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

