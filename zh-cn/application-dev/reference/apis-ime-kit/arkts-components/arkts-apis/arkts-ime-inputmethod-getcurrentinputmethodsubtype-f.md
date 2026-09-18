# getCurrentInputMethodSubtype

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getCurrentInputMethodSubtype

```TypeScript
function getCurrentInputMethodSubtype(): InputMethodSubtype
```

获取当前输入法的子类型。

**起始版本：** 9

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodSubtype](arkts-ime-inputmethodsubtype-i.md) | 返回当前输入法子类型对象。 |

**示例**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype();
```

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype(100);
  console.info('Succeeded in getting current input method subtype, id: ' + currentImeSubType.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getCurrentInputMethodSubtype. Code: ${error.code}, message: ${error.message}`);
}
```
