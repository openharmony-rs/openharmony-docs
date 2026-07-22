# SelectDialog

选择类弹出框，弹框中以列表或网格的形式提供可选的内容。

**起始版本：** 10

<!--Device-unnamed-export declare struct SelectDialog--><!--Device-unnamed-export declare struct SelectDialog-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialog, SelectDialog, ButtonOptions, PopoverOptions, TipsDialog, PopoverDialog, LoadingDialog, CustomContentDialog, ConfirmDialog } from '@kit.ArkUI';
```

## confirm

```TypeScript
confirm?: ButtonOptions
```

选择弹出框底部按钮。

**类型：** ButtonOptions

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialog-confirm?: ButtonOptions--><!--Device-SelectDialog-confirm?: ButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

选择弹出框内容。

默认不设置或设置为undefined，弹出框内容不显示。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialog-content?: ResourceStr--><!--Device-SelectDialog-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: CustomDialogController
```

选择弹出框控制器。

**说明：** 未使用@Require装饰，构造时不强制校验参数。

**类型：** CustomDialogController

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialog-controller: CustomDialogController--><!--Device-SelectDialog-controller: CustomDialogController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radioContent

```TypeScript
radioContent: Array<SheetInfo>
```

选择弹出框的子项内容列表，每个选择项支持设置文本和选中的回调事件。

**类型：** Array&lt;SheetInfo&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialog-radioContent: Array<SheetInfo>--><!--Device-SelectDialog-radioContent: Array<SheetInfo>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

选择弹出框的选中项。

取值范围：大于等于-1的整数。

默认值：-1，没有选中项。若设置数值小于-1，按没有选中项处理。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialog-selectedIndex?: number--><!--Device-SelectDialog-selectedIndex?: number-End-->

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

<!--Device-SelectDialog-theme?: Theme | CustomTheme--><!--Device-SelectDialog-theme?: Theme | CustomTheme-End-->

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

<!--Device-SelectDialog-themeColorMode?: ThemeColorMode--><!--Device-SelectDialog-themeColorMode?: ThemeColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

选择弹出框标题。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialog-title: ResourceStr--><!--Device-SelectDialog-title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

