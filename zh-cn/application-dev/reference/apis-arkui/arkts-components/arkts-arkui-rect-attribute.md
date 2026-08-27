# Rect属性/事件

除支持通用属性以及[图形绘制通用属性](../../../reference/apis-arkui/arkui-ts/ts-drawing-components-common.md)外，还支持以下 属性：

**继承/实现关系：** RectAttribute extends CommonShapeMethod<RectAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## radius

```TypeScript
radius(value: Length | Array<any>)
```

设置圆角半径大小，取值范围≥0，支持attributeModifier动态设置属性方法。该属性与 [radiusWidth](#radiuswidth)、[radiusHeight](#radiusheight)属性效果类似，在组合使用时优先于 radiusWidth和radiusHeight生效。异常值undefined、null、NaN和Infinity按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) \| Array & lt;any & gt; | 是 | 圆角半径大小。 默认值：0 默认单位：vp 异常值undefined、null、NaN和Infinity按照[[0, 0], [0, 0], [0, 0], [0, 0]]处理。<br>**起始版本：** 20 |

## radiusHeight

```TypeScript
radiusHeight(value: Length)
```

设置圆角的高度。仅设置radiusHeight时，圆角的高度和宽度相同。该属性与[radius](#radius)属性效果类似，当与radius组合使用时，radius属性优先于本属性生效。支 持attributeModifier动态设置属性方法。异常值undefined、null、NaN和Infinity按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 圆角的高度，取值范围≥0。 默认值：0 默认单位：vp。 异常值undefined、null、NaN和Infinity按照默认值处理。<br>**起始版本：** 20 |

## radiusWidth

```TypeScript
radiusWidth(value: Length)
```

设置圆角的宽度。仅设置radiusWidth时，圆角的宽度和高度相同。该属性与[radius](#radius)属性效果类似，当与radius组合使用时，radius属性优先于本属性生效。支持 attributeModifier动态设置属性方法。异常值undefined、null、NaN和Infinity按照默认值处理。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 圆角的宽度，取值范围≥0。 默认值：0 默认单位：vp。 异常值undefined、null、NaN和Infinity按照默认值处理。<br>**起始版本：** 20 |
