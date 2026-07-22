# CustomContentDialogV2

自定义内容区弹出框，同时支持定义操作区按钮样式。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct CustomContentDialogV2--><!--Device-unnamed-export declare struct CustomContentDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## buttons

```TypeScript
buttons?: AdvancedDialogV2Button[]
```

弹出框操作区按钮，最多支持4个按钮。

默认不显示。

**类型：** AdvancedDialogV2Button[]

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-buttons?: AdvancedDialogV2Button[]--><!--Device-CustomContentDialogV2-buttons?: AdvancedDialogV2Button[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentAreaPadding

```TypeScript
contentAreaPadding?: LocalizedPadding
```

弹出框内容区内边距。

默认不显示。

**类型：** LocalizedPadding

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-contentAreaPadding?: LocalizedPadding--><!--Device-CustomContentDialogV2-contentAreaPadding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentBuilder

```TypeScript
contentBuilder: CustomBuilder
```

弹出框内容。

**类型：** CustomBuilder

**起始版本：** 18

**装饰器类型：** @BuilderParam

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-contentBuilder: CustomBuilder--><!--Device-CustomContentDialogV2-contentBuilder: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

弹出框标题。

默认不显示。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-primaryTitle?: ResourceStr--><!--Device-CustomContentDialogV2-primaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

弹出框辅助文本。

默认不显示。

**说明：** 辅助文本超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-secondaryTitle?: ResourceStr--><!--Device-CustomContentDialogV2-secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

