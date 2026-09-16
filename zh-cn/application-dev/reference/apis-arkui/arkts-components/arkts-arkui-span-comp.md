# Span

作为Text、ContainerSpan组件的子组件，用于显示行内文本，支持对文本的字体、颜色、大小等样式进行细粒度设置。适用于在同一行文本中混合显示不同样式的场景，如不同字体颜色的文本、添加装饰线或阴影效果等。

> **说明：** > > 该组件从API version 10开始支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的属性。支持继承的属性仅包括：fontColor、fontSize、fontStyle、 > fontWeight、decoration、letterSpacing、textCase、fontFamily、textShadow。 > > 不支持[通用属性]](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)。若需设置通用属性， > 应使用Text进行设置，或改用属性字符串中的[CustomSpan](../arkts-apis/arkts-arkui-customspan-c.md)自行绘制。 > > [通用事件](arkts-arkui-commonmethod-c.md)只支持点击事件 > onClick和悬浮事件 > onHover。

## 子组件

无

## Span

```TypeScript
Span(value: string | Resource)
```

定义Span组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | 是 | 文本内容。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TextBackgroundStyle](arkts-arkui-textbackgroundstyle-i.md) | 定义Span的背景样式。 |

## 示例

```TypeScript
### 示例1（设置文本样式）

该示例展示了设置不同样式的文本效果以及Span配置点击事件。


```

```TypeScript
### 示例2（设置文本阴影）

从API version 11开始，该示例通过[textShadow](#textshadow11)属性展示了文本设置阴影的效果。


```

```TypeScript
### 示例3（设置背景样式）

从API version 11开始，该示例通过[textBackgroundStyle](#textbackgroundstyle11)属性展示了文本设置背景样式的效果。


```

```TypeScript
### 示例4（设置文本基线偏移量）

从API version 12开始，该示例通过[baselineOffset](#baselineoffset12)属性展示了文本设置不同基线偏移量的效果。


```

```TypeScript
### 示例5（设置文本可变字体的属性）

该示例通过[fontVariations](#fontvariations)属性设置可变字体的属性。

从API版本26.0.0开始，新增[fontVariations](#fontvariations)接口。
```
