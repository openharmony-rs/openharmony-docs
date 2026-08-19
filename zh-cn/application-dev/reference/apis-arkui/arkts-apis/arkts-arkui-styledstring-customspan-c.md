# CustomSpan

自定义绘制Span，仅提供基类，具体实现由开发者定义。 自定义绘制Span拖拽显示的缩略图为空白。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class CustomSpan--><!--Device-unnamed-export declare abstract class CustomSpan-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## invalidate

```TypeScript
invalidate(): void
```

主动刷新使用CustomSpan的Text组件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomSpan-invalidate(): void--><!--Device-CustomSpan-invalidate(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDraw

```TypeScript
abstract onDraw(context: DrawContext, drawInfo: CustomSpanDrawInfo): void
```

绘制自定义绘制Span。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomSpan-abstract onDraw(context: DrawContext, drawInfo: CustomSpanDrawInfo): void--><!--Device-CustomSpan-abstract onDraw(context: DrawContext, drawInfo: CustomSpanDrawInfo): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [DrawContext](arkts-arkui-graphics-drawcontext-c.md) | 是 |  |
| drawInfo | [CustomSpanDrawInfo](arkts-arkui-styledstring-customspandrawinfo-i.md) | 是 |  |

## onMeasure

```TypeScript
abstract onMeasure(measureInfo: CustomSpanMeasureInfo): CustomSpanMetrics
```

获取自定义绘制Span的尺寸大小。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomSpan-abstract onMeasure(measureInfo: CustomSpanMeasureInfo): CustomSpanMetrics--><!--Device-CustomSpan-abstract onMeasure(measureInfo: CustomSpanMeasureInfo): CustomSpanMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| measureInfo | [CustomSpanMeasureInfo](arkts-arkui-styledstring-customspanmeasureinfo-i.md) | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CustomSpanMetrics](arkts-arkui-styledstring-customspanmetrics-i.md) | 自定义绘制Span的尺寸信息。<br/>**说明：** <br/>最终的CustomSpan的高度是由当前Text组件的行高所决定的。当height不传值，则默认取 Text组件的fontSize的值作为CustomSpan的高度；当height大于当前行的其他子组件的高度时，此时height即为Text组件的行高。 |

