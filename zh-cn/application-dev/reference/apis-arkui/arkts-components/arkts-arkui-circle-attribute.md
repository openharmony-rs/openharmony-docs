# Circle属性/事件

除支持通用属性以及图形绘制通用属性外，还支持以下 属性：

**继承/实现关系：** CircleAttribute extends CommonShapeMethod<CircleAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## fill

```TypeScript
fill(value: ResourceColor | ColorMetrics)
```

设置填充区域的颜色，支持使用[ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md)描述颜色，可进行HDR提亮。支持 attributeModifier动态设置属性。不设置时，默认填充颜色为Color.Black。异常值undefined 、null、NaN和Infinity按照默认值处理。与通用属性foregroundColor同时设置时，后设置的属性生效。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorMetrics | 是 | 填充区域颜色。 默认值：Color.Black 异常值undefined、null、NaN和Infinity按照默认值处理。 |

## stroke

```TypeScript
stroke(value: ResourceColor | ColorMetrics)
```

设置边框颜色，支持使用[ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md)描述颜色，可进行HDR提亮。支持 attributeModifier动态设置属性。不设置时，默认边框颜色为Color.Transparent，即没有边框。 异常值undefined和null按照默认值处理，NaN和Infinity按照Color.Black处理。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| ColorMetrics | 是 | 边框颜色。 默认值：Color.Transparent 异常值undefined和null按照默认值处理，NaN和Infinity按照Color.Black处理。 |
