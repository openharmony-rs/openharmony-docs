# DrawingRenderingContext

DrawingRenderingContext对象与Canvas组件绑定后，可在Canvas组件上进行绘制， 绘制对象可以是形状、文本、图片等。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class DrawingRenderingContext--><!--Device-unnamed-export declare class DrawingRenderingContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(unit?: LengthMetricsUnit)
```

构造使用drawing接口进行绘制的Canvas画布对象，支持配置DrawingRenderingContext对象的单位模式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawingRenderingContext-constructor(unit?: LengthMetricsUnit)--><!--Device-DrawingRenderingContext-constructor(unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| unit | [LengthMetricsUnit](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | 否 | 用来配置DrawingRenderingContext对象的单位模式， 配置后无法更改。异常值undefined、NaN和Infinity按默认值处理。默认值：DEFAULT。 |

## invalidate

```TypeScript
invalidate(): void
```

使组件无效，触发组件的重新渲染。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DrawingRenderingContext-invalidate(): void--><!--Device-DrawingRenderingContext-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

