# Text

Text组件用于显示文本内容，支持设置字体样式、文本对齐、行高、装饰线等属性，支持图文混排、文本选择、文本识别等功能，适用于需要展示文本信息的各类应用场景。

## 子组件 可以包含[Span]{@link ./span}、[ImageSpan]{@link ./image_span}、[SymbolSpan]{@link ./symbol_span}和 [ContainerSpan]{@link ./container_span}子组件。 > **说明：** > > 使用[子组件](docroot://reference/apis-arkui/arkui-ts/ts-basic-components-text.md#子组件)实现 > [图文混排](docroot://ui/arkts-text-image-layout.md)场景。

## Text

```TypeScript
Text(content?: string | Resource, value?: TextOptions)
```

定义文本组件构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-TextInterface-(content?: string | Resource, value?: TextOptions): TextAttribute--><!--Device-TextInterface-(content?: string | Resource, value?: TextOptions): TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| Resource | 否 | 文本内容。当需要直接显示文本内容时传入此参数。包含子组件[Span]\_\_\_JSDOC\_LINK\_USD\_0\_\_\_或设置了 [属性字符串]\_\_\_JSDOC\_LINK\_USD\_1\_\_\_时，该参数不生效。 \_\_\_HTML\_TAG\_USD\_2\_\_\_默认值：' ' \_\_\_HTML\_TAG\_USD\_3\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_4\_\_\_显示内容的优先级：属性字符串>Span>Text的文本内容。  |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 文本组件初始化选项，用于配置文本控制器。当需要使用TextController的功能控制文本内容和选择时，传入此参数。 \_\_\_HTML\_TAG\_USD\_0\_\_\_默认值：不设置时，不使用文本控制器。 \_\_\_HTML\_TAG\_USD\_1\_\_\_ |

## 汇总

