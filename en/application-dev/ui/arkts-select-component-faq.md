# FAQs About Buttons and Selection Components
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyi0309-->
<!--Designer: @liyi0309-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->

This topic addresses frequently asked questions regarding buttons and selection components.

## How Are the Slider Thumb and Track of the Slider Component Aligned?

The **Slider** component supports three display styles defined by [SliderStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#sliderstyle). Both **SliderStyle.OutSet** and **SliderStyle.InSet** include visible slider thumbs. When the slider progress is at the minimum value, the alignment behavior differs between these two styles:

**SliderStyle.OutSet**: The thumb center aligns with the track endpoint.

![OutSet](figures/SliderOutset.jpg)

**SliderStyle.InSet**: The slider thumb aligns with the track centerline (midpoint of the track endpoint height).

![InSet](figures/SliderInset.jpg)

**Example**

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

## Inconsistent Default Font Weight When AttributeModifier Is Used to Set LabelStyle of a Button

**Symptom**

When **LabelStyle** is set for the **Button** component, the default font weight of the label text is inconsistent in different setting modes.

**Possible Causes**

There are two ways to set **LabelStyle**:
- Set [LabelStyle](../reference/apis-arkui/arkui-ts/ts-basic-components-button.md#labelstyle10) directly. In this case, the default value of the **weight** attribute in **font** is **FontWeight.Medium**, which corresponds to the value **500**.
- Set **LabelStyle** through the [AttributeModifier](../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md#attributemodifier) API. In this case, the default value of the **weight** attribute in **font** is **400**, which is different from the default value described in the **LabelStyle** description.

**Solution**

To avoid display differences caused by different setting ways, you are advised to explicitly specify the **weight** value when setting **LabelStyle** through the **AttributeModifier** API to ensure that the text style meets the expectation. The following is an example:

<!-- @[button_modifier_faq](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ButtonAttribute/entry/src/main/ets/pages/ButtonModifierFAQ.ets) -->

```ts

// pages/ButtonModifierFAQ.ets
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
      // Set labelStyle for the Button component. The default value of weight in the font attribute is 500.
      Button('DemoButtonTest')
        .width(100)
        .labelStyle({})
      Divider()
      // Set labelStyle via AttributeModifier. The default value of weight in the font attribute is 400.
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

![Differences between ButtonModifiers](figures/ButtonModifier.png)
