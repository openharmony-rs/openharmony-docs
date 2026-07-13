# Shape

绘制组件的父组件，父组件中会描述所有绘制组件均支持的通用属性。

1、绘制组件使用Shape作为父组件，实现类似SVG的效果。

2、绘制组件单独使用，用于在页面上绘制指定的图形。

> **说明：**

> 该组件从API version 20开始支持使用[AttributeUpdater]{@link AttributeUpdater}类的
> [updateConstructorParams](docroot://reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。


## Shape

```TypeScript
Shape(value?: PixelMap)
```

Use the new function to create Shape.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap | 否 |  |

## Shape

```TypeScript
Shape(value: PixelMap)
```

用于绘制Shape组件的构造函数。

从API version 9开始，该接口支持在ArkTS卡片中使用，卡片中不支持使用PixelMap对象。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap | 是 | 绘制目标，可将图形绘制在指定的PixelMap对象中，若未设置，则默认在当前绘制目标中进行绘制。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

## Shape

```TypeScript
Shape()
```

Called when a component is drawn.

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

- [ViewportRect](arkts-arkui-shape-viewportrect-i.md)
