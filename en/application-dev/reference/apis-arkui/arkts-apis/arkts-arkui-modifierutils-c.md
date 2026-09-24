# ModifierUtils

```TypeScript
export declare class ModifierUtils
```

ModifierUtils provides utility methods for modifier and attribute operations.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isInstanceOf

```TypeScript
static isInstanceOf<T extends CommonMethod<T>>(instance: T, componentName: string): boolean
```

Checks if the given instance is of the specified component type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | The instance to check. |
| componentName | string | Yes | The name of the component type to check against. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the instance is of the specified component type. Otherwise, returns false. @static |

**Examples**

```TypeScript
// xxx.ets
// Click the button and check the log to determine whether the component enters the exclusive branch.
import { ModifierUtils } from '@kit.ArkUI';

class MyModifier implements AttributeModifier<TextAttribute | ButtonAttribute> {
  isDark: boolean = false;

  constructor(dark?: boolean) {
    this.isDark = dark ?? false;
  }

  applyNormalAttribute(instance: TextAttribute | ButtonAttribute): void {
    if (ModifierUtils.isInstanceOf(instance, 'Text')) {
      console.info('This is TextAttribute');
      const textInstance = instance as TextAttribute;
      if (this.isDark) {
        textInstance.backgroundColor(Color.Blue);
      } else {
        textInstance.backgroundColor(Color.Green);
      }
    } else if (ModifierUtils.isInstanceOf(instance, 'Button')) {
      console.info('This is ButtonAttribute');
      const buttonInstance = instance as ButtonAttribute;
      if (this.isDark) {
        buttonInstance.type(ButtonType.Circle);
        buttonInstance.backgroundColor(Color.Blue);
      } else {
        buttonInstance.type(ButtonType.Normal);
        buttonInstance.backgroundColor(Color.Green);
      }
    }
  }
}

@Entry
@Component
struct MultiComponentAttributeDemo {
  @State myModifier: MyModifier = new MyModifier();

  build() {
    Column() {
      Text('Text')
        .fontSize(50)
        .attributeModifier(this.myModifier)
        .onClick(() => {
          this.myModifier.isDark = !this.myModifier.isDark;
        })
      Button('Button')
        .attributeModifier(this.myModifier)
        .onClick(() => {
          this.myModifier.isDark = !this.myModifier.isDark;
        })
    }
    .justifyContent(FlexAlign.SpaceEvenly)
    .width('100%')
    .height('50%')
  }
}
```
