# CanvasLineJoin

```TypeScript
export type CanvasLineJoin = 'bevel' | 'miter' | 'round'
```

定义长度不为0的两个连接部分（线段、圆弧和曲线）的类型。 'bevel': 在线段相连处使用三角形为底填充，每个部分矩形拐角独立。 'miter': 在相连部分的外边缘处进行延伸，使其相交于一点，形成一个菱形区域， 该属性可以通过设置miterLimit属性展现效果。 'round': 在线段相连处绘制一个扇形，扇形的圆角半径是线段的宽度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type CanvasLineJoin = 'bevel' | 'miter' | 'round'--><!--Device-unnamed-export type CanvasLineJoin = 'bevel' | 'miter' | 'round'-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| 'bevel' |  |
| 'miter' |  |
| 'round' |  |

