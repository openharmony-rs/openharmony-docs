# ExtendableText（可扩展的Text）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Text](./ts-basic-components-text.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableText，支持重写Text中的[属性](./ts-basic-components-text.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Text](./ts-basic-components-text.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableText } from '@kit.ArkUI';
```

## 子组件

可以包含[Span](ts-basic-components-span.md)、[ImageSpan](ts-basic-components-imagespan.md)、[SymbolSpan](ts-basic-components-symbolSpan.md)和[ContainerSpan](ts-basic-components-containerspan.md)子组件。

## 属性

自定义的Text扩展组件类支持重写Text的[属性](./ts-basic-components-text.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setTextOptions

setTextOptions(content?: string | Resource, value?: TextOptions): this

设置文本配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| content | string \| [Resource](ts-types.md#resource) | 否   |  文本内容。当不包含子组件[Span](ts-basic-components-span.md)和未设置[属性字符串](ts-universal-styled-string.md)时该参数生效。<br/>默认值：' '<br/>**说明：** <br/>显示内容的优先级：属性字符串>Span>Text的文本内容。 |
| value | [TextOptions](./ts-basic-components-text.md#textoptions11) | 否   | 文本组件初始化选项。<br/> 未设置时，则按照TextOptions中各参数的默认值配置。 |

## 事件

支持Text的[事件](./ts-basic-components-text.md#事件)和[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableText, TextOptions, Length, Entry, Component, Text, Column } from '@kit.ArkUI';

class MyText extends ExtendableText {
  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }

  // 自定义属性
  newAttribute(): this {
    super.height('50%');
    super.width('50%');
    return this;
  }
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      // 调用扩展组件
      MyText('Hello World')
        .fontSize(50)
        .newAttribute() // 调用自定义属性
      MyText('Hello ArkUI')
        .fontSize(30)
        .width() // 调用重写属性
        .height('50%')
    }
  }
}
```

