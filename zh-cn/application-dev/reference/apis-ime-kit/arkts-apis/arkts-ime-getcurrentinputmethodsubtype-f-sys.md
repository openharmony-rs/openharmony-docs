# getCurrentInputMethodSubtype（系统接口）

## getCurrentInputMethodSubtype

```TypeScript
function getCurrentInputMethodSubtype(userId?: number): InputMethodSubtype
```

获取指定用户的当前输入法子类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 否 | 用户ID。如果不提供：<br>- 如果调用者不是用户0的应用，该值默认为调用者的用户ID。<br>- 如果调用者是用户0的应用，该值默认为主屏幕的前台用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| InputMethodSubtype | 返回当前输入法子类型对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-指定的用户不存在) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-指定的用户未在前台) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-跨用户操作被拒绝) | cross-user operation denied.Only user 0 applications are authorized for this operation. |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

try {
  let currentImeSubType: InputMethodSubtype = inputMethod.getCurrentInputMethodSubtype(100);
  console.info('Succeeded in getting current input method subtype, id: ' + currentImeSubType.id);
} catch (err) {
  console.error(`Failed to getCurrentInputMethodSubtype. Code: ${err.code}, message: ${err.message}`);
}

```

