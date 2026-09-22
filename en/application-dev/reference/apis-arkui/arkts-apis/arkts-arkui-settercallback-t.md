# SetterCallback

```TypeScript
export declare type SetterCallback<T> = (newValue: T) => void
```

Defines a callback used to set a value.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | Parameter of the T type. |

**Examples**

```TypeScript
import { MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: MutableBinding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // MutableBinding supports mutability. You can change the value of num2.value
        num1.value += 1;
      })
  }
}

@Entry
@ComponentV2
struct CompV2 {
  @Local number1: number = 10;

  build() {
    Column() {
      Text('parent component')

      CustomButton(
        // The second parameter of the UIUtils.makeBinding function must be a SetterCallback.
        UIUtils.makeBinding<number>(
          () => this.number1, // GetterCallback
          (val: number) => {
            this.number1 = val;
          }) // SetterCallback is mandatory. Otherwise, a runtime error will be thrown.
      )
    }
  }
}
```
