# GetterCallback

```TypeScript
export declare type GetterCallback<T> = () => T
```

Defines a callback used to obtain a value.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { Binding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: Binding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // num1.value += 1; will throw an error because the Binding element does not support modification.
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 5;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        // The first parameter of the UIUtils.makeBinding function must be a GetterCallback.
        UIUtils.makeBinding<number>(
          () => this.number1 // GetterCallback
        )
      )
    }
  }
}
```
