# CanvasFillRule

```TypeScript
declare type CanvasFillRule = "evenodd" | "nonzero"
```

定义用于确定点是在路径内还是路径外的填充样式算法的类型。取值类型为下表类型中的并集。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type CanvasFillRule = "evenodd" | "nonzero"--><!--Device-unnamed-declare type CanvasFillRule = "evenodd" | "nonzero"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| "evenodd" | 奇偶规则。此规则通过从画布上的某点向任意方向发射一条射线，并统计图形路径与射线的交点数量来判断该点是否在图形内部。如果交点数量是奇数，则该点在图形内部，否则在图形外部。 |
| "nonzero" | 非零规则。此规则通过从画布上的某点向任意方向发射一条射线，并检查图形路径与射线的交点来判断该点是否在图形内部。初始计数为0，为路径的每一段线段指定一个方向值，每当路径从左向右穿过射线时加1，从右向左穿过时减1。如果最终的结果是0，则该点在图形外部，否则在图形内部。 |

