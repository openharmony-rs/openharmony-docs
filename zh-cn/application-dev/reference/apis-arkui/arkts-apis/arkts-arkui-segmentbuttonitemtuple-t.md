# SegmentButtonItemTuple

```TypeScript
declare type SegmentButtonItemTuple = ItemRestriction<SegmentButtonTextItem> | ItemRestriction<SegmentButtonIconItem> | ItemRestriction<SegmentButtonIconTextItem>
```

用于保存按钮信息的元组的联合类型。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| ItemRestriction&lt;SegmentButtonTextItem&gt; | A A A 仅文本按钮信息的元组。 |
| ItemRestriction&lt;SegmentButtonIconItem&gt; | A A A 仅图标按钮信息的元组。 |
| ItemRestriction&lt;SegmentButtonIconTextItem&gt; | A A A 图标+文本按钮信息的元组。 |

