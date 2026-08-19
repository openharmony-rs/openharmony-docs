# SubHeaderV2SelectOnSelect

```TypeScript
export type SubHeaderV2SelectOnSelect = (selectedIndex: number, selectedContent?: string) => void
```

下拉菜单选中某一项的回调类型。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type SubHeaderV2SelectOnSelect = (selectedIndex: number, selectedContent?: string) => void--><!--Device-unnamed-export type SubHeaderV2SelectOnSelect = (selectedIndex: number, selectedContent?: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectedIndex | number | 是 | 选中的下拉菜单项的索引值，索引从0开始计数。 |
| selectedContent | string | 否 | 选中的下拉菜单项的文本内容，即用户选择的菜单项显示的文本。 |

