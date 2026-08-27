# ContainerSpan

Text组件的子组件，用于统一管理多个Span、ImageSpan的背景色及圆角弧度，适用于需要为文本片段和图片组合设置统一背 景样式的场景。

## 子组件

可以包含Span、ImageSpan 子组件。

## ContainerSpan

```TypeScript
ContainerSpan()
```

定义ContainerSpan组件构造函数。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

## 示例

从API version 11开始，该示例通过[textBackgroundStyle](#textbackgroundstyle)属性展示了文本设置背景样式的效果。

```TypeScript
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

从API version 12开始，该示例通过[attributeModifier](#attributemodifier12)属性展示了文本设置背景样式的效果。

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
