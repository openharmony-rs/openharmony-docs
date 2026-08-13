# ConfirmDialogV2

信息确认类弹出框，用于反馈错误或提示信息。当操作未正确执行（如网络错误、电池电量过低）或用户操作不当时（如指纹录入），弹出此类对话框进行提示。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare struct ConfirmDialogV2--><!--Device-unnamed-export declare struct ConfirmDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checkTips

```TypeScript
@Param
  checkTips?: ResourceStr
```

checkbox的提示内容。 默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Param  checkTips?: ResourceStr--><!--Device-ConfirmDialogV2-@Param  checkTips?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## checked

```TypeScript
@Param
  checked?: boolean
```

checked为true时，表示checkbox已选中，为false时，表示未选中。 默认值：false

**类型：** boolean

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Param  checked?: boolean--><!--Device-ConfirmDialogV2-@Param  checked?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@Param
  content?: ResourceStr
```

确认弹出框内容。 默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Param  content?: ResourceStr--><!--Device-ConfirmDialogV2-@Param  content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onCheckedChange

```TypeScript
@Param
  onCheckedChange?: AdvancedDialogV2OnCheckedChange
```

checkbox的选中状态改变事件。 默认无事件。

**类型：** [AdvancedDialogV2OnCheckedChange](arkts-arkui-advanceddialogv2oncheckedchange-t.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Param  onCheckedChange?: AdvancedDialogV2OnCheckedChange--><!--Device-ConfirmDialogV2-@Param  onCheckedChange?: AdvancedDialogV2OnCheckedChange-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
@Param
  primaryButton?: AdvancedDialogV2Button
```

确认弹出框左侧按钮。 默认不显示。

**类型：** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Param  primaryButton?: AdvancedDialogV2Button--><!--Device-ConfirmDialogV2-@Param  primaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
@Param
  secondaryButton?: AdvancedDialogV2Button
```

确认弹出框右侧按钮。 默认不显示。

**类型：** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Param  secondaryButton?: AdvancedDialogV2Button--><!--Device-ConfirmDialogV2-@Param  secondaryButton?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
@Require
  @Param
  title: ResourceStr
```

确认弹出框标题。 **说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ConfirmDialogV2-@Require  @Param  title: ResourceStr--><!--Device-ConfirmDialogV2-@Require  @Param  title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

