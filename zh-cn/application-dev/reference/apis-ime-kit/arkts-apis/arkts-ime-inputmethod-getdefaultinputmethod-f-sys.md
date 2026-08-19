# getDefaultInputMethod（系统接口）

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
import { inputMethodEngine } from '@kit.IMEKit';
import { InputMethodListDialog, PatternOptions, Pattern } from '@kit.IMEKit';
import { PanelInfo, PanelType, PanelFlag } from '@kit.IMEKit';
import { InputMethodExtraConfig } from '@kit.IMEKit';
import { inputMethodSystemPanelManager } from '@kit.IMEKit';
```

## getDefaultInputMethod

```TypeScript
function getDefaultInputMethod(userId?: int): InputMethodProperty
```

获取指定用户的默认输入法。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethod-function getDefaultInputMethod(userId?: int): InputMethodProperty--><!--Device-inputMethod-function getDefaultInputMethod(userId?: int): InputMethodProperty-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 否 | 用户ID。如果不提供： <br>- 如果调用者不是用户0的应用，该值默认为调用者的用户ID。 <br>- 如果调用者是用户0的应用，该值默认为主屏幕的前台用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 返回默认输入法属性对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12800023](../errorcode-inputmethod-framework.md#12800023-指定的用户不存在) | the specified user does not exist. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-跨用户操作被拒绝) | cross-user operation denied. Only user 0 applications are authorized for this operation. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause: a system error, such as null pointer, IPC exception. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-指定的用户未在前台) | the specified user is not in the foreground. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let defaultIme: inputMethod.InputMethodProperty = inputMethod.getDefaultInputMethod(100);
  console.info('Succeeded in getting default input method, name: ' + defaultIme.name + ', id: ' + defaultIme.id);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to getDefaultInputMethod. Code: ${error.code}, message: ${error.message}`);
}
```

