# ToolBarItem

可以使用**ToolBarItem**组件，通过[toolbar](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-toolbar.md#toolbar)通用属性向标题栏中添加toolbar item。 > **说明** > > 该组件通常与[toolbar](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-toolbar.md#toolbar)通用属性一起使用。

## 子组件 该组件可以包含单个子组件。

## ToolBarItem

```TypeScript
ToolBarItem(options?: ToolBarItemOptions)
```

默认在标题栏对应分栏开头位置创建工具栏项，分栏位置由绑定该[toolbar](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-toolbar.md#toolbar)属性的组件所在分栏位置而定。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolBarItemInterface-(options?: ToolBarItemOptions): ToolBarItemAttribute--><!--Device-ToolBarItemInterface-(options?: ToolBarItemOptions): ToolBarItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ToolBarItemOptions](arkts-arkui-toolbaritemoptions-i.md) | 否 | ToolBarItem**的可选参数，包括[ToolBarItemPlacement](arkts-arkui-toolbaritemplacement-e.md#ToolBarItemPlacement)类型的**placement**参数。<br>默认值：**placement: ToolBarItemPlacement.TOP_BAR_LEADING |

## 汇总

- [ToolBarItemOptions](arkts-arkui-toolbaritemoptions-i.md)
- [ToolBarItemPlacement](arkts-arkui-toolbaritemplacement-e.md)
