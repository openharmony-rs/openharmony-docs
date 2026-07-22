# ConfirmDialogV2

信息确认类弹出框，操作未正确执行（如网络错误、电池电量过低），或未正确操作时（如指纹录入），反馈的错误或提示信息。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct ConfirmDialogV2--><!--Device-unnamed-export declare struct ConfirmDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## checkTips

```TypeScript
checkTips?: ResourceStr
```

checkbox的提示内容。

默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-checkTips?: ResourceStr--><!--Device-ConfirmDialogV2-checkTips?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
checked?: boolean
```

checked为true时，表示checkbox已选中，为false时，表示未选中。

默认值：false

**类型：** boolean

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-checked?: boolean--><!--Device-ConfirmDialogV2-checked?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

确认弹出框内容。

默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-content?: ResourceStr--><!--Device-ConfirmDialogV2-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
onCheckedChange?: AdvancedDialogV2OnCheckedChange
```

checkbox的选中状态改变事件。

默认无事件。

**类型：** AdvancedDialogV2OnCheckedChange

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange--><!--Device-ConfirmDialogV2-onCheckedChange?: AdvancedDialogV2OnCheckedChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: AdvancedDialogV2Button
```

确认弹出框左侧按钮。

默认不显示。

**类型：** AdvancedDialogV2Button

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-primaryButton?: AdvancedDialogV2Button--><!--Device-ConfirmDialogV2-primaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: AdvancedDialogV2Button
```

确认弹出框右侧按钮。

默认不显示。

**类型：** AdvancedDialogV2Button

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-secondaryButton?: AdvancedDialogV2Button--><!--Device-ConfirmDialogV2-secondaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

确认弹出框标题。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-title: ResourceStr--><!--Device-ConfirmDialogV2-title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

