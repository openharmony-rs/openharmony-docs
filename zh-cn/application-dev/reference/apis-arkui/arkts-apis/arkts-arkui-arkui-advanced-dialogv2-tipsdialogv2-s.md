# TipsDialogV2

提示弹出框，即为带图形确认弹出框，必要时可通过图形化方式展现确认弹出框。适用于需要图形化方式展示的重要提示场景，如应用卸载确认等。

**起始版本：** 18

<!--Device-unnamed-export declare struct TipsDialogV2--><!--Device-unnamed-export declare struct TipsDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## checkTips

```TypeScript
@Param
  checkTips?: ResourceStr
```

选择框的提示内容。 默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  checkTips?: ResourceStr--><!--Device-TipsDialogV2-@Param  checkTips?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
@Param
  checked?: boolean
```

checked为true时，表示选择框已选中。checked为false时，表示选择框未选中。 默认值：false

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  checked?: boolean--><!--Device-TipsDialogV2-@Param  checked?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@Param
  content?: ResourceStr
```

提示弹出框内容。 默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  content?: ResourceStr--><!--Device-TipsDialogV2-@Param  content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageBorderColor

```TypeScript
@Param
  imageBorderColor?: ColorMetrics
```

图片描边颜色。 默认值：Color.Black

**类型：** [ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  imageBorderColor?: ColorMetrics--><!--Device-TipsDialogV2-@Param  imageBorderColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageBorderWidth

```TypeScript
@Param
  imageBorderWidth?: LengthMetrics
```

图片描边宽度。 默认无描边效果。

**类型：** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  imageBorderWidth?: LengthMetrics--><!--Device-TipsDialogV2-@Param  imageBorderWidth?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageRes

```TypeScript
@Require
  @Param
  imageRes: ResourceStr | PixelMap
```

展示的图片。

**类型：** ResourceStr \| PixelMap

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Require  @Param  imageRes: ResourceStr | PixelMap--><!--Device-TipsDialogV2-@Require  @Param  imageRes: ResourceStr | PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageSize

```TypeScript
@Param
  imageSize?: SizeOptions
```

自定义图片尺寸。 默认值：64*64vp

**类型：** SizeOptions

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  imageSize?: SizeOptions--><!--Device-TipsDialogV2-@Param  imageSize?: SizeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
@Param
  onCheckedChange?: AdvancedDialogV2OnCheckedChange
```

选择框的选中状态改变事件。 默认无事件。

**类型：** [AdvancedDialogV2OnCheckedChange](arkts-arkui-advanceddialogv2oncheckedchange-t.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  onCheckedChange?: AdvancedDialogV2OnCheckedChange--><!--Device-TipsDialogV2-@Param  onCheckedChange?: AdvancedDialogV2OnCheckedChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
@Param
  primaryButton?: AdvancedDialogV2Button
```

提示弹出框左侧按钮。 默认不显示。

**类型：** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  primaryButton?: AdvancedDialogV2Button--><!--Device-TipsDialogV2-@Param  primaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
@Param
  secondaryButton?: AdvancedDialogV2Button
```

提示弹出框右侧按钮。 默认不显示。

**类型：** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  secondaryButton?: AdvancedDialogV2Button--><!--Device-TipsDialogV2-@Param  secondaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
@Param
  title?: ResourceStr
```

提示弹出框标题。 默认不显示。 **说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-TipsDialogV2-@Param  title?: ResourceStr--><!--Device-TipsDialogV2-@Param  title?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

