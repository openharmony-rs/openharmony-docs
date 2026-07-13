# OnItemDragStartCallback

```TypeScript
declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder
```

定义在onItemDragStart中使用的回调类型。

**起始版本：** 23

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | ItemDragInfo | 是 | 被拖拽项的信息。 |
| itemIndex | number | 是 | 拖动项的索引号。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CustomBuilder | @syscap SystemCapability.ArkUI.ArkUI.Full@FaAndStageModel@crossplatform@atomicservice |

