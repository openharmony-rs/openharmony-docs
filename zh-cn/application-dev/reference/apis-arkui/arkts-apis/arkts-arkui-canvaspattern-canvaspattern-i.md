# CanvasPattern

描述一个模板的不透明对象，该对象通过createPattern()方法创建。

**起始版本：** 11

<!--Device-unnamed-export interface CanvasPattern--><!--Device-unnamed-export interface CanvasPattern-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

使用Matrix2D对象作为参数，对当前CanvasPattern进行矩阵变换。

**起始版本：** 11

**模型约束：** 此接口仅可在FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasPattern-setTransform(transform?: Matrix2D): void--><!--Device-CanvasPattern-setTransform(transform?: Matrix2D): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | [Matrix2D](arkts-arkui-canvaspattern-matrix2d-c.md) | 否 | 变换矩阵。 |

