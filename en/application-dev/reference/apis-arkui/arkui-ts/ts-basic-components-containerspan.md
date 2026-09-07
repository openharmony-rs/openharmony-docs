# ContainerSpan
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiangyuan6-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=92567145241181b97abe57e944e177355e50f4eb translatedAt=2026-09-03T03:46:43.728Z -->

A child component of the [Text](ts-basic-components-text.md) component, used to manage the background colors and rounded corners of multiple [Span](ts-basic-components-span.md) and [ImageSpan](ts-basic-components-imagespan.md) components in a unified manner. It applies to scenarios where a unified background style needs to be set for a combination of text segments and images.

> **NOTE**
>
> - This component is supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

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

Sets the text background style. Child components inherit this attribute value when they do not set it. When this API is not used, the default background color is Color.Transparent and the default rounded corner radius is 0.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| style | [TextBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11) | Yes | Text background style, used to set the text background color and rounded corner radius of Span and ImageSpan in the ContainerSpan component. Child components inherit this style when this attribute is not set. |

### attributeModifier<sup>12+</sup>

attributeModifier(modifier: AttributeModifier\<ContainerSpanAttribute>)

Creates an attribute modifier.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                               | Mandatory| Description                                                        |
| ------ | --------------------------------------------------- | ---- | ------------------------------------------------------------ |
| modifier  | [AttributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<ContainerSpanAttribute> | Yes   | Dynamically sets the attributes of the component. Developers need to customize a class that inherits from the AttributeModifier interface, receive a ContainerSpanAttribute instance in the applyNormalAttribute method, and dynamically modify the attribute values of ContainerSpan. |

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
          color: '#7F007DFF',
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
    this.textBackgroundStyle({ color: '#7F007DFF', radius: '12vp' });
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