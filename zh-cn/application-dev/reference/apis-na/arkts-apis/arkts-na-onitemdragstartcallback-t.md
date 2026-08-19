# OnItemDragStartCallback

```TypeScript
export type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: int) => (CustomBuilder | undefined)
```

Defines the callback type used in onItemDragStart.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: int) => (CustomBuilder | undefined)--><!--Device-unnamed-export type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: int) => (CustomBuilder | undefined)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [ItemDragInfo](arkts-na-common-itemdraginfo-i.md) | 是 | Information about the dragged item. |
| itemIndex | int | 是 | The index number of the dragged item. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (CustomBuilder \| undefined) | - |

