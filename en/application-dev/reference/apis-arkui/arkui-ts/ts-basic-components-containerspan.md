# ContainerSpan
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @pssea-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

As a child of the [Text](ts-basic-components-text.md) component, the **ContainerSpan** component is used to manage the background colors and rounded corners of multiple [Span](ts-basic-components-span.md) and [ImageSpan](ts-basic-components-imagespan.md) components in a unified manner.

> **NOTE**
>
> This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.

## Child Components

This component can contain the [Span](ts-basic-components-span.md) and [ImageSpan](ts-basic-components-imagespan.md) child components.

## APIs

ContainerSpan()

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

Only the following attributes are supported.

### textBackgroundStyle

textBackgroundStyle(style: TextBackgroundStyle)

Sets the text background style. If this attribute is not separately set for a child component, the child component inherits the settings from the component.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| style  | [TextBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11) | Yes  | Text background style.<br>Default value:<br>{<br>  color: Color.Transparent,<br>  radius: 0<br>} |

### attributeModifier<sup>12+</sup>

attributeModifier(modifier: AttributeModifier\<ContainerSpanAttribute>)

Creates an attribute modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| modifier  | [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<ContainerSpanAttribute> | Yes  | Modifier for dynamically setting attributes on the current component.|

## Events

The [universal events](ts-component-general-events.md) are not supported.

## Example
### Example 1: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](#textbackgroundstyle) attribute, available since API version 11.

```ts
// xxx.ets
@Component
@Entry
struct Index {
  build() {
    Column() {
      Text() {
        ContainerSpan() {
          // Replace $r('app.media.app_icon') with the image resource file you use.
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

### Example 2: Setting the Background Style Using attributeModifier

This example demonstrates how to set the background style for text using the [attributeModifier](#attributemodifier12) attribute, available since API version 12.

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
          // Replace $r('app.media.startIcon') with the image resource file you use.
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
