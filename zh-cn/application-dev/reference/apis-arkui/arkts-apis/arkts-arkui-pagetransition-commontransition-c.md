# CommonTransition

页面转场通用动效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class CommonTransition--><!--Device-unnamed-export declare class CommonTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## opacity

```TypeScript
opacity(value: double): this
```

设置入场的起点透明度值或者退场的终点透明度值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonTransition-opacity(value: double): this--><!--Device-CommonTransition-opacity(value: double): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | double | 是 | 设置入场的起点透明度值或者退场的终点透明度值。&lt;br/&gt;取值范围：[0, 1] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## scale

```TypeScript
scale(value: ScaleOptions): this
```

设置页面转场时的缩放效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonTransition-scale(value: ScaleOptions): this--><!--Device-CommonTransition-scale(value: ScaleOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ScaleOptions](../arkts-components/arkts-arkui-scaleoptions-i.md) | 是 | 设置页面转场时的缩放效果，为入场时起点和退场时终点的值。&lt;br/&gt;- x：横向放大倍数（或缩小比例）。&lt;br/&gt;- y：纵向放大倍数（或缩小比例）。&lt;br/&gt;- z：竖向放大倍数（或缩小比例）。&lt;br/&gt;- centerX、centerY缩放中心点。centerX和centerY默认值是"50%"，即默认以页面的中心点为旋转中心点。&lt;br/&gt;- 中心点为(0, 0)代表页面的左 上角。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## slide

```TypeScript
slide(value: SlideEffect): this
```

设置页面转场时的滑入滑出效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonTransition-slide(value: SlideEffect): this--><!--Device-CommonTransition-slide(value: SlideEffect): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SlideEffect](arkts-arkui-pagetransition-slideeffect-e.md) | 是 | 页面转场时的滑入滑出效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

## translate

```TypeScript
translate(value: TranslateOptions): this
```

设置页面转场时的平移效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CommonTransition-translate(value: TranslateOptions): this--><!--Device-CommonTransition-translate(value: TranslateOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TranslateOptions](../arkts-components/arkts-arkui-translateoptions-i.md) | 是 | 设置页面转场时的平移效果，为入场时起点和退场时终点的值，和slide同时设置时默认生效slide。&lt;br/&gt;- x：横向的平移距离。&lt;br/&gt;- y：纵向 的平移距离。&lt;br/&gt;- z：竖向的平移距离。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前组件。 |

