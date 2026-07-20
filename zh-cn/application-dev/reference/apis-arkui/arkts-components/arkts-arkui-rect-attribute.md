# Rect属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** RectAttribute extends [CommonShapeMethod<RectAttribute>](CommonShapeMethod<RectAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class RectAttribute extends CommonShapeMethod<RectAttribute>--><!--Device-unnamed-declare class RectAttribute extends CommonShapeMethod<RectAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="radius"></a>
## radius

```TypeScript
radius(value: Length | Array<any>)
```

设置圆角半径大小，取值范围≥0，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectAttribute-radius(value: Length | Array<any>): RectAttribute--><!--Device-RectAttribute-radius(value: Length | Array<any>): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) \| Array&lt;any&gt; | 是 | 圆角半径大小。<br/>默认值：0<br/>默认单位：vp <br/>异常值undefined和null按照[[0, 0], [0, 0], [0, 0], [0, 0]]处理。<br>**起始版本：** 20 |

<a id="radiusheight"></a>
## radiusHeight

```TypeScript
radiusHeight(value: Length)
```

设置圆角的高度，仅设置高时宽高一致，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。 异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectAttribute-radiusHeight(value: Length): RectAttribute--><!--Device-RectAttribute-radiusHeight(value: Length): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 圆角的高度，取值范围≥0。<br/>默认值：0<br/>默认单位：vp <br/>异常值undefined按照默认值处理。<br>**起始版本：** 20 |

<a id="radiuswidth"></a>
## radiusWidth

```TypeScript
radiusWidth(value: Length)
```

设置圆角的宽度，仅设置宽时宽高一致，支持[attributeModifier](arkts-arkui-commonmethod-c.md#attributemodifier-1)动态设置属性方法。 异常值按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RectAttribute-radiusWidth(value: Length): RectAttribute--><!--Device-RectAttribute-radiusWidth(value: Length): RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 圆角的宽度，取值范围≥0。<br/>默认值：0<br/>默认单位：vp <br/>异常值undefined按照默认值处理。<br>**起始版本：** 20 |

