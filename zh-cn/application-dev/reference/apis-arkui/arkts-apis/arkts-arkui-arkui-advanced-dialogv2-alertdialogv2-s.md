# AlertDialogV2

操作确认类弹出框。当触发一个将产生严重后果的不可逆操作时，如删除、重置、取消编辑、停止等，会触发该类弹出框提示。

**起始版本：** 18

**装饰器类型：** @ComponentV2

<!--Device-unnamed-export declare struct AlertDialogV2--><!--Device-unnamed-export declare struct AlertDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { AdvancedDialogV2OnCheckedChange, LoadingDialogV2, AdvancedDialogV2Button, AdvancedDialogV2ButtonAction, AlertDialogV2, CustomContentDialogV2, PopoverDialogV2Options, PopoverDialogV2, SelectDialogV2, PopoverDialogV2OnVisibleChange, TipsDialogV2, AdvancedDialogV2ButtonOptions, ConfirmDialogV2 } from '@kit.ArkUI';
```

## content

```TypeScript
content: ResourceStr
```

确认弹出框内容。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Require、@Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogV2-content: ResourceStr--><!--Device-AlertDialogV2-content: ResourceStr-End-->

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

<!--Device-AlertDialogV2-primaryButton?: AdvancedDialogV2Button--><!--Device-AlertDialogV2-primaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryTitle

```TypeScript
primaryTitle?: ResourceStr
```

确认弹出框一级标题。

默认不显示。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogV2-primaryTitle?: ResourceStr--><!--Device-AlertDialogV2-primaryTitle?: ResourceStr-End-->

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

<!--Device-AlertDialogV2-secondaryButton?: AdvancedDialogV2Button--><!--Device-AlertDialogV2-secondaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryTitle

```TypeScript
secondaryTitle?: ResourceStr
```

确认弹出框二级标题。

默认不显示。

**说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**装饰器类型：** @Param

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-AlertDialogV2-secondaryTitle?: ResourceStr--><!--Device-AlertDialogV2-secondaryTitle?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

