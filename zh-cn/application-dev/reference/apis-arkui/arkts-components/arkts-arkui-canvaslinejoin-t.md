# CanvasLineJoin

```TypeScript
declare type CanvasLineJoin = "bevel" | "miter" | "round"
```

定义长度不为0的两个连接部分（线段、圆弧和曲线）的类型。取值类型为下表类型中的并集。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type CanvasLineJoin = "bevel" | "miter" | "round"--><!--Device-unnamed-declare type CanvasLineJoin = "bevel" | "miter" | "round"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| "bevel" | 在线段相连处使用三角形为底填充，每个部分矩形拐角独立。 |
| "miter" | 在相连部分的外边缘处进行延伸，使其相交于一点，形成一个菱形区域，该属性可以通过设置miterLimit属性展现效果。 |
| "round" | 在线段相连处绘制一个扇形，扇形的圆角半径是线段的宽度。 |

