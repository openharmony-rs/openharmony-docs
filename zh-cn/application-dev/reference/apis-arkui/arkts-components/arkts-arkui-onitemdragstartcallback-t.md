# OnItemDragStartCallback

```TypeScript
declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder
```

开始拖拽列表或网格元素时触发的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder--><!--Device-unnamed-declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 拖拽点的信息。  |
| itemIndex | number | 是 | 被拖拽列表元素索引值。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回CustomBuilder用于构建被拖拽元素的拖拽图。返回void表示不能拖拽。 |

