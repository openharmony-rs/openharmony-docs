# ContainerSpan属性/事件

仅支持以下属性：不支持[通用事件](arkts-arkui-commonmethod-c.md)。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<ContainerSpanAttribute>)
```

设置组件的动态属性。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](arkts-arkui-attributemodifier-i.md)&lt;[ContainerSpanAttribute](arkts-arkui-containerspan-attribute.md)&gt; | 是 | 动态设置组件的属性。开发者需自定义类继承AttributeModifier接口，在 applyNormalAttribute方法中接收ContainerSpanAttribute实例并动态修改ContainerSpan的属性值。 |

## textBackgroundStyle

```TypeScript
textBackgroundStyle(style: TextBackgroundStyle)
```

设置文本背景样式。子组件在不设置该属性时，将继承此属性值。未通过该接口设置时，默认背景颜色为Color.Transparent，圆角弧度为0。

> **说明：**
> 
> 从API version 12开始，该接口支持在attributeModifier中调用。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [TextBackgroundStyle](arkts-arkui-textbackgroundstyle-i.md) | 是 | 文本背景样式，用于设置ContainerSpan组件内Span和ImageSpan的文本背景颜色和圆角弧度。子组件不设置该属性时将继承此样式。 |
