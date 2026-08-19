# GetItemMainSizeByIndex

```TypeScript
export type GetItemMainSizeByIndex = (index: int) => double
```

根据index获取指定Item的主轴大小。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type GetItemMainSizeByIndex = (index: int) => double--><!--Device-unnamed-export type GetItemMainSizeByIndex = (index: int) => double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | FlowItem在WaterFlow中的索引。<br/>。 <br>取值范围：[0, 子节点总数-1]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 指定index的FlowItem的主轴大小，纵向瀑布流时为高度，横向瀑布流时为宽度，单位vp。 |

