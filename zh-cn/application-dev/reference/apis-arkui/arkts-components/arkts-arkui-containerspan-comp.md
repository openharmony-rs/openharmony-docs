# ContainerSpan

Text组件的子组件，用于统一管理多个Span、ImageSpan的背景色及圆角弧度，适用于需要为文本片段和图片组合设置统一背景样式的场景。

## 子组件

可以包含Span、ImageSpan 子组件。

## ContainerSpan

```TypeScript
ContainerSpan()
```

定义ContainerSpan组件构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

## 示例

```TypeScript
### 示例1（设置背景样式）

从API version 11开始，该示例通过[textBackgroundStyle](#textbackgroundstyle)属性展示了文本设置背景样式的效果。


```

```TypeScript
### 示例2（通过attributeModifier设置背景样式）

从API version 12开始，该示例通过[attributeModifier](#attributemodifier12)属性展示了文本设置背景样式的效果。
```
