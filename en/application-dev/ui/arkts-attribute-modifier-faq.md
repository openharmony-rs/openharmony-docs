# FAQs About Dynamic Attribute Setting
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @sd-wu-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=362dac8e3cbda6d43d3f16dbaa7d559f172df172 translatedAt=2026-11-05T03:17:08.966Z pushedAt=2026-11-05T08:31:34.251Z nl=1 -->

This topic addresses common issues related to dynamic attribute setting.

## Using AttributeModifier to Set Component Dynamic Attributes Causes JS Crash

**Symptom**

A [JS crash](../dfx/jscrash-guidelines.md) occurs after **AttributeModifier** is used to [set dynamic attributes](../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md) for a component.

<!--RP1-->
![](figures/jscrash_happened.png)
<!--RP1End-->

**Solution**

Go to the error log as prompted, view the error cause, and rectify the fault. For details, see the code example below. 

**Code Example**

This example binds **AttributeModifier** to a **Button** to demonstrate a scenario where **AttributeModifier** throws an exception when setting an unsupported attribute. After running the sample code, a JS Crash error occurs. Refer to the animation below to jump to the specific error scenario. In this example, deleting the **reuseId**-related code allows it to run normally.

```ts
// xxx.ets
// Set the custom AttributeModifier for the Button component attributes.
class MyButtonModifier implements AttributeModifier<ButtonAttribute> {

  applyNormalAttribute(instance: ButtonAttribute): void {
    instance.reuseId('String') // Deleting this line will allow the application to run normally.
    instance.backgroundColor(Color.Red)
  }
}

@Entry
@Component
struct AttributeDemo {
  @State modifier: MyButtonModifier = new MyButtonModifier();

  build() {
    Row() {
      Column() {
        Button('Button')
          .attributeModifier(this.modifier)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```
![attributeModifier_error](figures/attributeModifier_error.gif)