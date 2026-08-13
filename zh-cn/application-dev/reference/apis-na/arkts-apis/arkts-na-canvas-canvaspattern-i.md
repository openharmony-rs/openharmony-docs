# CanvasPattern

一个Object对象，使用createPattern方法创建，通过指定图像和重复方式创建图片填充的模板。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CanvasPattern--><!--Device-unnamed-export declare interface CanvasPattern-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

使用Matrix2D对象作为参数，对当前CanvasPattern进行矩阵变换。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasPattern-setTransform(transform?: Matrix2D): void--><!--Device-CanvasPattern-setTransform(transform?: Matrix2D): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | [Matrix2D](../../apis-arkui/arkts-apis/arkts-arkui-matrix2d-c.md) | 否 | 转换矩阵。&lt;br&gt;异常值undefined和null按无效值不做矩阵变换处理。 &lt;br&gt;默认值：不做矩阵变换 |

