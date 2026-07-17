# getSystemInputMethodConfigAbility（系统接口）

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## getSystemInputMethodConfigAbility

```TypeScript
function getSystemInputMethodConfigAbility(userId?: number): ElementName
```

获取指定用户的系统输入法设置界面Ability信息。用于启动系统输入法配置界面。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputMethod-function getSystemInputMethodConfigAbility(userId?: int): ElementName--><!--Device-inputMethod-function getSystemInputMethodConfigAbility(userId?: int): ElementName-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 否 | 用户ID。如果不提供：<br>- 如果调用者不是用户0的应用，该值默认为调用者的用户ID。<br>- 如果调用者是用户0的应用，该值默认为主屏幕的前台用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ElementName](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-elementname-t.md) | 系统输入法设置界面Ability的ElementName。 |

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
import { bundleManager } from '@kit.AbilityKit';

try {
  let inputMethodConfig: bundleManager.ElementName = inputMethod.getSystemInputMethodConfigAbility(100);
  console.info('Succeeded in getting system input method config ability, bundleName: ' + inputMethodConfig.bundleName);
} catch (err) {
  console.error(`Failed to getSystemInputMethodConfigAbility. Code: ${err.code}, message: ${err.message}`);
}

```

