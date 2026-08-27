# SetterCallback

```TypeScript
export declare type SetterCallback<T> = (newValue: T) => void
```

设置值的回调方法。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | 要设置的新值，当绑定值被修改时传入此参数。 |

**示例**

```TypeScript
import { MutableBinding, UIUtils } from '@kit.ArkUI';

@Builder
function CustomButton(num1: MutableBinding<number>) {
  Row() {
    Button(`Custom Button: ${num1.value}`)
      .onClick(() => {
        // MutableBinding支持可变，可以修改num1.value
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
        // 对于UIUtils.makeBinding函数的第二个参数需要传入SetterCallback
        UIUtils.makeBinding<number>(
          () => this.number1, // GetterCallback
          (val: number) => {
            this.number1 = val;
          }) // SetterCallback 必须提供，否则触发时会造成运行时错误
      )
    }
  }
}
```
