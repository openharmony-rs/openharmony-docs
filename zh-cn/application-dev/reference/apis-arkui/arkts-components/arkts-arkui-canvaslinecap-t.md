# CanvasLineCap

```TypeScript
declare type CanvasLineCap = "butt" | "round" | "square"
```

定义绘制每条线段端点的类型。取值类型为下表类型中的并集。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| "butt" | 线条两端为平行线，不额外扩展。 |
| "round" | 在线条两端延伸半个圆，直径等于线宽。 |
| "square" | 在线条两端延伸一个矩形，宽度等于线宽的一半，高度等于线宽。 |

