# Text

Text组件用于显示文本内容，支持设置字体样式、文本对齐、行高、装饰线等属性，支持图文混排、文本选择、文本识别等功能，适用于需要展示文本信息的各类应用场景。

## 子组件 可以包含Span、ImageSpan、SymbolSpan和 ContainerSpan子组件。 > **说明：** > > 使用[子组件](../../../reference/apis-arkui/arkui-ts/ts-basic-components-text.md#子组件)实现 > [图文混排](../../../ui/arkts-text-image-layout.md)场景。

## Text

```TypeScript
Text(content?: string | Resource, value?: TextOptions)
```

定义文本组件构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextInterface-(content?: string | Resource, value?: TextOptions): TextAttribute--><!--Device-TextInterface-(content?: string | Resource, value?: TextOptions): TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| Resource | 否 | 文本内容。当需要直接显示文本内容时传入此参数。包含子组件Span或设置了 属性字符串时，该参数不生效。 <br>默认值：' ' <br>**说明：** <br>显示内容的优先级：属性字符串>Span>Text的文本内容。 |
| value | [TextOptions](arkts-arkui-textoptions-i.md) | 否 | 文本组件初始化选项，用于配置文本控制器。当需要使用TextController的功能控制文本内容和选择时，传入此参数。 <br>默认值：不设置时，不使用文本控制器。 <br> |

## 汇总

- [TextMarqueeOptions](arkts-arkui-textmarqueeoptions-i.md)
- [TextOptions](arkts-arkui-textoptions-i.md)
- [TextOverflowOptions](arkts-arkui-textoverflowoptions-i.md)
- [MarqueeStartPolicy](arkts-arkui-marqueestartpolicy-e.md)
- [MarqueeState](arkts-arkui-marqueestate-e.md)
- [MarqueeUpdatePolicy](arkts-arkui-marqueeupdatepolicy-e.md)
- [TextResponseType](arkts-arkui-textresponsetype-e.md)
- [TextSpanType](arkts-arkui-textspantype-e.md)
