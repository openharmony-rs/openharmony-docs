# FAQs About Dynamic Attribute Setting
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangjunman1-->
<!--Designer: @sunbees-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

This topic addresses common issues related to dynamic attribute setting.

## JS Crash Occurs When AttributeModifier Is Used to Set Dynamic Attributes for a Component

**Symptom**

A [JS crash](../dfx/jscrash-guidelines.md) occurs after **AttributeModifier** is used to [set dynamic attributes](../reference/apis-arkui/arkui-ts/ts-universal-attributes-attribute-modifier.md) for a component.

<!--RP1-->
![](figures/jscrash_happened.png)
<!--RP1End-->

**Solution**

Go to the error log as prompted, view the error cause, and rectify the fault. For details, see the code example below.

**Code Example**

In this example, a button is bound to **AttributeModifier** to demonstrate the scenario where an exception is thrown when an unsupported attribute is set. After the code is executed, a JS crash error is reported. In this example, deleting the code related to **reuseId** will allow the application to run normally.

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
struct attributeDemo {
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
