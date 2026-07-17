# switchInputMethodWithUserId（系统接口）

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## switchInputMethodWithUserId

```TypeScript
function switchInputMethodWithUserId(bundleName: string, subtypeId?: string, userId?: number): Promise<void>
```

切换输入法，使用promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethod-function switchInputMethodWithUserId(bundleName: string, subtypeId?: string, userId?: int): Promise<void>--><!--Device-inputMethod-function switchInputMethodWithUserId(bundleName: string, subtypeId?: string, userId?: int): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 目标输入法的包名。 |
| subtypeId | string | 否 | 输入法子类型的ID。如果不设置该参数，则切换到使用默认子类型的目标输入法。 |
| userId | number | 否 | 用户ID。如果不提供：<br>- 如果调用者不是用户0的应用，该值默认为调用者的用户ID。<br>- 如果调用者是用户0的应用，该值默认为主屏幕的前台用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-配置持久化失败) | configuration persistence error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |
| [12800023](../errorcode-inputmethod-framework.md#12800023-指定的用户不存在) | the specified user does not exist. |
| [12800024](../errorcode-inputmethod-framework.md#12800024-指定的用户未在前台) | the specified user is not in the foreground. |
| [12800025](../errorcode-inputmethod-framework.md#12800025-跨用户操作被拒绝) | cross-user operation denied.Only user 0 applications are authorized for this operation. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

inputMethod.switchInputMethodWithUserId('com.example.keyboard', 'subtype_001', 100).then(() => {
  console.info('Succeeded in switching input method.');
}).catch((err: BusinessError) => {
  console.error(`Failed to switchInputMethodWithUserId, code: ${err.code}, message: ${err.message}`);
});

```

