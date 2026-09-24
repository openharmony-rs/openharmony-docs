# ContainerSpan

As a child of the [Text](arkts-arkui-text-comp.md#text) component, the **ContainerSpan** component is used to manage the background colors and rounded corners of multiple [Span](arkts-arkui-span-comp.md#span) and [ImageSpan](arkts-arkui-imagespan-comp.md#image_span) components in a unified manner.

## ContainerSpan

```TypeScript
ContainerSpan()
```

Defines the constructor of ContainerSpan.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

## Examples

### Example 1: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](#textbackgroundstyle) attribute, available since API version 11.



```TypeScript
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

### Example 2: Setting the Background Style Using attributeModifier

This example demonstrates how to set the background style for text using the [attributeModifier](#attributemodifier12) attribute, available since API version 12.

```TypeScript
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
