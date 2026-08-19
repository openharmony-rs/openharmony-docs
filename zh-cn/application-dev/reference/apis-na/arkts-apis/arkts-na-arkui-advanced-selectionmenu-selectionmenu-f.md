# SelectionMenu

## 导入模块

```TypeScript
```

## SelectionMenu

```TypeScript
@Builder
export declare function SelectionMenu(options: SelectionMenuOptions): void
```

入参为空时，文本选择菜单组件SelectionMenu内容区大小及组件大小为零。表现例如，富文本组件 [RichEditor](../../../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md)使用 [bindSelectionMenu](../../../reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md#bindselectionmenu)接口绑定一 个SelectionMenu的右键菜单，则右键富文本组件区域时无任何菜单弹出。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function SelectionMenu(options: SelectionMenuOptions): void--><!--Device-unnamed-@Builderexport declare function SelectionMenu(options: SelectionMenuOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | SelectionMenuOptions | 是 | 文本选择菜单可选项。 |

