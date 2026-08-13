# OnSelectCallback

```TypeScript
export type OnSelectCallback = (index: int, selectStr: string) => void
```

Select组件选择项的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnSelectCallback = (index: int, selectStr: string) => void--><!--Device-unnamed-export type OnSelectCallback = (index: int, selectStr: string) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 选中的项的索引。 |
| selectStr | string | 是 | 选中的项的文本内容。 |

