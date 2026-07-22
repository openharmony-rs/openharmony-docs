# ConfirmDialog

信息确认类弹出框，操作未正确执行（如网络错误、电池电量过低），或未正确操作时（如指纹录入），反馈的错误或提示信息。

**起始版本：** 10

<!--Device-unnamed-export declare struct ConfirmDialog--><!--Device-unnamed-export declare struct ConfirmDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialog, SelectDialog, ButtonOptions, PopoverOptions, TipsDialog, PopoverDialog, LoadingDialog, CustomContentDialog, ConfirmDialog } from '@kit.ArkUI';
```

## checkTips

```TypeScript
checkTips?: ResourceStr
```

checkbox的提示内容。

默认不设置或设置为undefined，checkbox的提示内容不显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-checkTips?: ResourceStr--><!--Device-ConfirmDialog-checkTips?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

确认弹出框内容。

默认不设置或设置为undefined，确认弹出框内容不显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-content?: ResourceStr--><!--Device-ConfirmDialog-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

确认弹出框控制器。

**说明：** 未使用@Require装饰，构造时不强制校验参数。

**类型：** CustomDialogController

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-controller: CustomDialogController--><!--Device-ConfirmDialog-controller: CustomDialogController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## isChecked

```TypeScript
@Prop isChecked?: boolean
```

value为true时，表示checkbox已选中，value为false时，表示未选中。

默认值：false

**类型：** boolean

**起始版本：** 10

**装饰器类型：** @Prop

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-@Prop isChecked?: boolean--><!--Device-ConfirmDialog-@Prop isChecked?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
onCheckedChange?: Callback<boolean>
```

checkbox的选中状态改变事件回调。回调参数类型为boolean，true表示checkbox已选中，false表示checkbox未选中。

**类型：** Callback&lt;boolean&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-onCheckedChange?: Callback<boolean>--><!--Device-ConfirmDialog-onCheckedChange?: Callback<boolean>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: ButtonOptions
```

确认弹出框左侧按钮。

默认不设置或设置为undefined，确认弹出框左侧按钮不显示。

**类型：** ButtonOptions

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-primaryButton?: ButtonOptions--><!--Device-ConfirmDialog-primaryButton?: ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: ButtonOptions
```

确认弹出框右侧按钮。

默认不设置或设置为undefined，确认弹出框右侧按钮不显示。

**类型：** ButtonOptions

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-secondaryButton?: ButtonOptions--><!--Device-ConfirmDialog-secondaryButton?: ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: Theme | CustomTheme
```

主题信息，可以是CustomTheme或从onWillApplyTheme中获取的Theme实例。

**类型：** Theme \| CustomTheme

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-theme?: Theme | CustomTheme--><!--Device-ConfirmDialog-theme?: Theme | CustomTheme-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## themeColorMode

```TypeScript
themeColorMode?: ThemeColorMode
```

自定义弹出框深浅色模式。

默认值：ThemeColorMode.SYSTEM

**类型：** ThemeColorMode

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-themeColorMode?: ThemeColorMode--><!--Device-ConfirmDialog-themeColorMode?: ThemeColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

确认弹出框标题。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialog-title: ResourceStr--><!--Device-ConfirmDialog-title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

