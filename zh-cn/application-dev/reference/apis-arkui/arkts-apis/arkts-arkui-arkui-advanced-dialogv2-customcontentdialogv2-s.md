# CustomContentDialogV2

自定义内容区弹出框，同时支持定义操作区按钮样式。适用于需要展示复杂或自定义内容的场景，如用户协议确认、表单输入等。

**起始版本：** 18

<!--Device-unnamed-export declare struct CustomContentDialogV2--><!--Device-unnamed-export declare struct CustomContentDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AlertDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonOptions, AdvancedDialogV2ButtonAction, AdvancedDialogV2OnCheckedChange, ConfirmDialogV2, LoadingDialogV2, SelectDialogV2, TipsDialogV2, CustomContentDialogV2, PopoverDialogV2, PopoverDialogV2OnVisibleChange, PopoverDialogV2Options } from '@kit.ArkUI';
```

## buttons

```TypeScript
@Param
  buttons?: AdvancedDialogV2Button[]
```

弹出框操作区按钮，最多支持4个按钮。 默认不显示。

**类型：** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)[]

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-@Param  buttons?: AdvancedDialogV2Button[]--><!--Device-CustomContentDialogV2-@Param  buttons?: AdvancedDialogV2Button[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentAreaPadding

```TypeScript
@Param
  contentAreaPadding?: LocalizedPadding
```

弹出框内容区内边距。 默认不显示。

**类型：** LocalizedPadding

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-@Param  contentAreaPadding?: LocalizedPadding--><!--Device-CustomContentDialogV2-@Param  contentAreaPadding?: LocalizedPadding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentBuilder

```TypeScript
@BuilderParam
  contentBuilder: CustomBuilder
```

弹出框内容。

**类型：** CustomBuilder

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-@BuilderParam  contentBuilder: CustomBuilder--><!--Device-CustomContentDialogV2-@BuilderParam  contentBuilder: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
@Param
  primaryTitle?: ResourceStr
```

弹出框标题。 默认不显示。 **说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-@Param  primaryTitle?: ResourceStr--><!--Device-CustomContentDialogV2-@Param  primaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
@Param
  secondaryTitle?: ResourceStr
```

弹出框辅助文本。 默认不显示。 **说明：** 辅助文本超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-CustomContentDialogV2-@Param  secondaryTitle?: ResourceStr--><!--Device-CustomContentDialogV2-@Param  secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

