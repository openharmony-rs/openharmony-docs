# getInputMethodSetting

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getInputMethodSetting

```TypeScript
function getInputMethodSetting(): InputMethodSetting
```

获取客户端设置实例[InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getSetting](arkts-ime-inputmethod-getsetting-f.md#getsetting-1)

<!--Device-inputMethod-function getInputMethodSetting(): InputMethodSetting--><!--Device-inputMethod-function getInputMethodSetting(): InputMethodSetting-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodSetting](arkts-ime-inputmethod-inputmethodsetting-i.md) | 返回当前客户端设置实例。 |

**示例：**

```TypeScript
let inputMethodSetting: inputMethod.InputMethodSetting = inputMethod.getInputMethodSetting();

```

