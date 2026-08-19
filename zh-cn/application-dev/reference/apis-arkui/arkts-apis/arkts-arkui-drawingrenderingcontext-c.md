# DrawingRenderingContext

DrawingRenderingContext对象与Canvas组件绑定后，可在Canvas组件上进行绘制，绘制对象可以是形状、文本、图片等。

**起始版本：** 12

<!--Device-unnamed-declare class DrawingRenderingContext--><!--Device-unnamed-declare class DrawingRenderingContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(unit?: LengthMetricsUnit)
```

构造使用drawing接口进行绘制的Canvas画布对象，支持配置DrawingRenderingContext对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawingRenderingContext-constructor(unit?: LengthMetricsUnit)--><!--Device-DrawingRenderingContext-constructor(unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | LengthMetricsUnit | 否 | 用来配置DrawingRenderingContext对象的单位模式，配置后无法更改， 配置方法同 [CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。 <br>异常值undefined、NaN和Infinity按默认值处理。 <br>默认值：DEFAULT。 |

## invalidate

```TypeScript
invalidate(): void
```

使组件无效，触发组件的重新渲染。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DrawingRenderingContext-invalidate(): void--><!--Device-DrawingRenderingContext-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

