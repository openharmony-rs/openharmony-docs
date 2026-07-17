# getDefaultInputMethod

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getDefaultInputMethod

```TypeScript
function getDefaultInputMethod(): InputMethodProperty
```

获取默认输入法。

**起始版本：** 11

<!--Device-inputMethod-function getDefaultInputMethod(): InputMethodProperty--><!--Device-inputMethod-function getDefaultInputMethod(): InputMethodProperty-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 返回默认输入法属性对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
let defaultIme: inputMethod.InputMethodProperty = inputMethod.getDefaultInputMethod();

```

