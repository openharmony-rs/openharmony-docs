# Circle属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** CircleAttribute extends [CommonShapeMethod<CircleAttribute>](CommonShapeMethod<CircleAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class CircleAttribute extends CommonShapeMethod<CircleAttribute>--><!--Device-unnamed-declare class CircleAttribute extends CommonShapeMethod<CircleAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="fill"></a>
## fill

```TypeScript
fill(value: ResourceColor | ColorMetrics)
```

Sets the color of the fill area.An invalid value is handled as the default value.If this attribute and the universal attribute foregroundColor are both set, whichever is set later takes effect.

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CircleAttribute-fill(value: ResourceColor | ColorMetrics): T--><!--Device-CircleAttribute-fill(value: ResourceColor | ColorMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorMetrics | 是 | Color of the fill area<br>Default value : Color.Black. |

<a id="stroke"></a>
## stroke

```TypeScript
stroke(value: ResourceColor | ColorMetrics)
```

Sets the stroke color.If this attribute is not set, the component does not have any stroke.If the value is invalid, no stroke will be drawn.

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-CircleAttribute-stroke(value: ResourceColor | ColorMetrics): T--><!--Device-CircleAttribute-stroke(value: ResourceColor | ColorMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorMetrics | 是 | Stroke color. |

