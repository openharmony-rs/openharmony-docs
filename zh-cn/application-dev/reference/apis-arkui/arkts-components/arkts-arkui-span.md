# Span

作为[Text]{@link text}、[ContainerSpan]{@link container_span}组件的子组件，用于显示行内文本的组件。

> **说明：**

> 该组件从API version 10开始支持继承父组件Text的属性，即如果子组件未设置属性且父组件设置属性，则继承父组件设置的属性。支持继承的属性仅包括：fontColor、fontSize、fontStyle、
> fontWeight、decoration、letterSpacing、textCase、fontFamily、textShadow。
>
> 不支持[通用属性]{@link common}。若需设置通用属性，应使用[Text]{@link text}进行设置，或改用[属性字符串]{@link styled_string}中的
> [CustomSpan]{@link CustomSpan}自行绘制。
>
> [通用事件]{@link common}只支持点击事件
> [onClick]{@link CommonMethod#onClick(event: Callback<ClickEvent>, distanceThreshold: number)}和悬浮事件
> [onHover]{@link CommonMethod#onHover}。

## 子组件

无

## Span

```TypeScript
Span(value: string | Resource)
```

定义Span组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanInterface-(value: string | Resource): SpanAttribute--><!--Device-SpanInterface-(value: string | Resource): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 文本内容。  |

## 汇总

- [TextBackgroundStyle](arkts-arkui-span-textbackgroundstyle-i.md)
