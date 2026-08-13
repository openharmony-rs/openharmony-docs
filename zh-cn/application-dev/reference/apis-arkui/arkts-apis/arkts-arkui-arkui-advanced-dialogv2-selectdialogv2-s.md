# SelectDialogV2

选择类弹出框，弹框中以列表或网格的形式提供可选的内容。适用于需要用户从多个选项中选择一个的场景，如选择语言、选择地区等。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export declare struct SelectDialogV2--><!--Device-unnamed-export declare struct SelectDialogV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## confirm

```TypeScript
@Param
  confirm?: AdvancedDialogV2Button
```

选择弹出框底部按钮。 默认不显示。

**类型：** [AdvancedDialogV2Button](arkts-arkui-arkui-advanced-dialogv2-advanceddialogv2button-c.md)

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-@Param  confirm?: AdvancedDialogV2Button--><!--Device-SelectDialogV2-@Param  confirm?: AdvancedDialogV2Button-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## content

```TypeScript
@Param
  content?: ResourceStr
```

选择弹出框内容。默认不显示。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-@Param  content?: ResourceStr--><!--Device-SelectDialogV2-@Param  content?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radioContent

```TypeScript
@Require
  @Param
  radioContent: SheetInfo[]
```

选择弹出框的子项内容列表，每个选择项支持设置文本和选中的回调事件。

**类型：** SheetInfo[]

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-@Require  @Param  radioContent: SheetInfo[]--><!--Device-SelectDialogV2-@Require  @Param  radioContent: SheetInfo[]-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
@Param
  selectedIndex?: number
```

选择弹出框的选中项，基于0的索引（0表示第一个选项）。 默认值：-1，没有选中项。若设置数值不在取值范围，按没有选中项处理。 取值范围：小于选择弹出框的子项内容列表长度。

**类型：** number

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-@Param  selectedIndex?: number--><!--Device-SelectDialogV2-@Param  selectedIndex?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
@Require
  @Param
  title: ResourceStr
```

选择弹出框标题。 **说明：** 标题超过两行会显示“...”。

**类型：** ResourceStr

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SelectDialogV2-@Require  @Param  title: ResourceStr--><!--Device-SelectDialogV2-@Require  @Param  title: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

