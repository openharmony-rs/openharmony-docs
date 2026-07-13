# CanvasPattern

一个Object对象，使用
[createPattern](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md#createpattern)
方法创建，通过指定图像和重复方式创建图片填充的模板。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setTransform

```TypeScript
setTransform(transform?: Matrix2D): void
```

使用Matrix2D对象作为参数，对当前CanvasPattern进行矩阵变换。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| transform | Matrix2D | 否 | 转换矩阵。<br>异常值undefined和null按无效值不做矩阵变换处理。<br>默认值：不做矩阵变换。 |

