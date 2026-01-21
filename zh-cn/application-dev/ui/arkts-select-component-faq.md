# 按钮与选择组件常见问题
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

本文档介绍按钮与选择组件的常见问题并提供参考。

## Slider组件滑块与滑轨是如何对齐的

Slider的滑块与滑轨显示样式[SliderStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#sliderstyle枚举说明)有三种，其中SliderStyle.OutSet与SliderStyle.InSet存在滑块。Slider的滑动条进度为最小值时，滑块对齐方式如下：

SliderStyle.OutSet模式下，滑块的中心与滑轨的端点对齐，示例图如下：

![OutSet示意图](figures/SliderOutset.jpg)

SliderStyle.InSet模式下，滑块与滑轨的中心对齐，即距离端点滑轨高度的一半的位置，示例图如下：

![InSet示意图](figures/SliderInset.jpg)

**示例**

```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Slider({
        style: SliderStyle.OutSet
      })
        .blockSize({
          width: 20,
          height: 20
        })
        .trackThickness(50)
      Slider({
        style: SliderStyle.InSet
      })
        .blockSize({
          width: 20,
          height: 20
        })
        .trackThickness(50)
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用AttributeModifier设置Button的LabelStyle时，默认字体粗细与直接设置不一致

**问题现象**

在Button组件中设置LabelStyle时，采用不同设置方式会出现Label文本默认字体粗细显示不一致的现象。

**可能原因**

设置LabelStyle有两种方式，其中：
- 直接设置[LabelStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#labelstyle10对象说明)。此时font属性中的weight默认值为FontWeight.Medium，对应数值500。
- 通过[AttributeModifier](../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier)接口设置。此时font属性中的weight默认值为400，与LabelStyle对象说明中的默认值存在差异。

**解决措施**

为避免不同设置方式导致的显示差异，建议在通过AttributeModifier接口设置LabelStyle时，显式指定weight的值，以确保文本样式符合预期，具体示例如下。

```ts
class MyButtonModifier1 implements AttributeModifier<ButtonAttribute> {
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.labelStyle({});
  }
}

class MyButtonModifier2 implements AttributeModifier<ButtonAttribute> {
  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.labelStyle({
      font: {
        weight: FontWeight.Medium
      }
    });
  }
}

@Entry
@Component
struct Index {
  @State modifier1: MyButtonModifier1 = new MyButtonModifier1();
  @State modifier2: MyButtonModifier2 = new MyButtonModifier2();

  build() {
    Column() {
      Text('normal')
      Button('DemoButtonTest')
        .width(100)
        .labelStyle({})
      Divider()
      Text('modifier1')
      Button('DemoButtonTest')
        .width(100)
        .attributeModifier(this.modifier1)
      Text('modifier2')
      Button('DemoButtonTest')
        .width(100)
        .attributeModifier(this.modifier2)
    }.height('100%')
  }
}
```

![ButtonModifier差异示意图](figures/ButtonModifier.png)