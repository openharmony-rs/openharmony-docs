# SelectDialogV2

选择类弹出框，弹框中以列表或网格的形式提供可选的内容。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct SelectDialogV2--><!--Device-unnamed-export declare struct SelectDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## confirm

```TypeScript
confirm?: AdvancedDialogV2Button
```

选择弹出框底部按钮。

默认不显示。

**类型：** AdvancedDialogV2Button

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-confirm?: AdvancedDialogV2Button--><!--Device-SelectDialogV2-confirm?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
content?: ResourceStr
```

选择弹出框内容。默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-content?: ResourceStr--><!--Device-SelectDialogV2-content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radioContent

```TypeScript
radioContent: SheetInfo[]
```

选择弹出框的子项内容列表，每个选择项支持设置文本和选中的回调事件。

**类型：** SheetInfo[]

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-radioContent: SheetInfo[]--><!--Device-SelectDialogV2-radioContent: SheetInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex?: number
```

选择弹出框的选中项。

默认值：-1，没有选中项。若设置数值不在取值范围，按没有选中项处理。

取值范围：小于选择弹出框的子项内容列表长度。

**类型：** number

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-selectedIndex?: number--><!--Device-SelectDialogV2-selectedIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title: ResourceStr
```

选择弹出框标题。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-title: ResourceStr--><!--Device-SelectDialogV2-title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

