# ContainerSpan
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

[Text](ts-basic-components-text.md)组件的子组件，用于统一管理多个[Span](ts-basic-components-span.md)、[ImageSpan](ts-basic-components-imagespan.md)的背景色及圆角弧度。

> **说明：**
>
> - 该组件从API version 11开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。

## 子组件

可以包含[Span](ts-basic-components-span.md)、[ImageSpan](ts-basic-components-imagespan.md) 子组件。

## 接口

ContainerSpan()

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

## 属性

仅支持以下属性：

### textBackgroundStyle

ArkTS-Dyn: textBackgroundStyle(style: TextBackgroundStyle)

ArkTS-Sta: textBackgroundStyle(style: TextBackgroundStyle | undefined)

设置文本背景样式。子组件在不设置该属性时，将继承此属性值。

>**说明：**
>
> 从API version 12开始，该接口支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                | 必填 | 说明                                                         |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| style  | ArkTS-Dyn: [TextBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11对象说明)<br/>ArkTS-Sta: [TextBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11对象说明) \| undefined | 是   | 文本背景样式。<br />默认值：<br />{<br />  color: Color.Transparent,<br />  radius: 0<br />}<br/>设置undefined时恢复默认值。 |

### attributeModifier<sup>12+</sup>

ArkTS-Dyn: attributeModifier(modifier: AttributeModifier\<ContainerSpanAttribute>)

ArkTS-Sta: attributeModifier(modifier: AttributeModifier\<ContainerSpanAttribute> | undefined)

设置组件的动态属性。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：** 

| 参数名 | 类型                                                | 必填 | 说明                                                         |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| modifier  | ArkTS-Dyn: [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<ContainerSpanAttribute><br/>ArkTS-Sta: [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<ContainerSpanAttribute> \| undefined | 是   | 动态设置组件的属性。<br/>取值为undefined时，按当前组件的属性方法默认值处理。 |

## 事件

不支持[通用事件](ts-component-general-events.md)。

## 示例
### 示例1（设置背景样式）

从API version 11开始，该示例通过[textBackgroundStyle](#textbackgroundstyle)属性展示了文本设置背景样式的效果。

```ts
// xxx.ets
@Component
@Entry
struct Index {
  build() {
    Column() {
      Text() {
        ContainerSpan() {
          // $r('app.media.app_icon')需要替换为开发者所需的图像资源文件。
          ImageSpan($r('app.media.app_icon'))
            .width('40vp')
            .height('40vp')
            .verticalAlign(ImageSpanAlignment.CENTER)
          Span('   Hello World !   ').fontSize('16fp').fontColor(Color.White)
        }
        .textBackgroundStyle({
          color: "#7F007DFF",
          radius: {
            topLeft: 12,
            topRight: 12,
            bottomLeft: 12,
            bottomRight: 12
          }
        })
      }
    }.width('100%').alignItems(HorizontalAlign.Center)
  }
}
```

![imagespan](figures/container_span.png)

### 示例2（通过attributeModifier设置背景样式）

从API version 12开始，该示例通过[attributeModifier](#attributemodifier12)属性展示了文本设置背景样式的效果。

```ts
import { ContainerSpanModifier } from '@kit.ArkUI';

class MyContainerSpanModifier extends ContainerSpanModifier {
  applyNormalAttribute(instance: ContainerSpanAttribute): void {
    super.applyNormalAttribute?.(instance);
    this.textBackgroundStyle({ color: "#7F007DFF", radius: "12vp" });
  }
}

@Entry
@Component
struct ContainerSpanModifierExample {
  @State containerSpanModifier: ContainerSpanModifier = new MyContainerSpanModifier();

  build() {
    Column() {
      Text() {
        ContainerSpan() {
          // $r('app.media.startIcon')需要替换为开发者所需的图像资源文件。
          ImageSpan($r('app.media.startIcon'))
            .width('40vp')
            .height('40vp')
            .verticalAlign(ImageSpanAlignment.CENTER)
          Span(' I\'m ContainerSpan attributeModifier ').fontSize('16fp').fontColor(Color.White)
        }.attributeModifier(this.containerSpanModifier as MyContainerSpanModifier)
      }
    }.width('100%').alignItems(HorizontalAlign.Center)
  }
}
```

![imagespan](figures/container_attributeModifier.png)