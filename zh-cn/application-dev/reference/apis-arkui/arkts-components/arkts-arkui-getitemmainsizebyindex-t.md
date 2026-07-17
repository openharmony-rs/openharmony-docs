# GetItemMainSizeByIndex

```TypeScript
declare type GetItemMainSizeByIndex = (index: number) => number
```

根据index获取指定Item的主轴大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type GetItemMainSizeByIndex = (index: number) => number--><!--Device-unnamed-declare type GetItemMainSizeByIndex = (index: number) => number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | FlowItem在WaterFlow中的索引。<br/>取值范围：[0, 子节点总数-1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 指定index的FlowItem的主轴大小，纵向瀑布流时为高度，横向瀑布流时为宽度，单位vp。 |

