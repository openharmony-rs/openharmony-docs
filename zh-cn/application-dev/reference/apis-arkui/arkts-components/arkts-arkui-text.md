# Text

显示一段文本的组件。

## 子组件

可以包含[Span]{@link span}、[ImageSpan]{@link image_span}、[SymbolSpan]{@link symbol_span}和[ContainerSpan]{@link container_span}子组件。

> **说明：**  
>  
> 使用[子组件](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-text.md#子组件)实现  
> [图文混排](docroot://ui/arkts-text-image-layout.md)场景。

## Text

```TypeScript
Text(content?: string | Resource, value?: TextOptions)
```

定义文本组件构造函数。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextInterface-(content?: string | Resource, value?: TextOptions): TextAttribute--><!--Device-TextInterface-(content?: string | Resource, value?: TextOptions): TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| Resource | 否 | 文本内容。当不包含子组件[Span]{@link span}和未设置[属性字符串]{@link styled_string}时该参数生效。<br/>默认值：' '<br/>**说明：** <br/>显示内容的优先级：属性字符串&gt;Span&gt;Text的文本内容。 |
| value | TextOptions | 否 | 文本组件初始化选项。<br/> |

## 汇总

- [TextMarqueeOptions](arkts-arkui-text-textmarqueeoptions-i.md)
- [TextOptions](arkts-arkui-text-textoptions-i.md)
- [TextOverflowOptions](arkts-arkui-text-textoverflowoptions-i.md)
- [MarqueeStartPolicy](arkts-arkui-text-marqueestartpolicy-e.md)
- [MarqueeState](arkts-arkui-text-marqueestate-e.md)
- [MarqueeUpdatePolicy](arkts-arkui-text-marqueeupdatepolicy-e.md)
- [TextResponseType](arkts-arkui-text-textresponsetype-e.md)
- [TextSpanType](arkts-arkui-text-textspantype-e.md)
