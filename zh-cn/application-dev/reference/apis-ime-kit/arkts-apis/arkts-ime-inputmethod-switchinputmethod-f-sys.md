# switchInputMethod（系统接口）

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

<a id="switchinputmethod"></a>
## switchInputMethod

```TypeScript
function switchInputMethod(bundleName: string, subtypeId?: string): Promise<void>
```

切换输入法，使用promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchInputMethod(bundleName: string, subtypeId?: string): Promise<void>--><!--Device-inputMethod-function switchInputMethod(bundleName: string, subtypeId?: string): Promise<void>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 目标输入法包名。 |
| subtypeId | string | 否 | 输入法子类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-配置持久化失败) | configuration persistence error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { InputMethodSubtype } from '@kit.IMEKit';

async function switchInputMethodWithSubtype() {
  // 1. 获取当前输入法
  const currentIme: inputMethod.InputMethodProperty | undefined = inputMethod.getCurrentInputMethod();
  if (!currentIme) {
    console.error("Failed to get current input method");
    return;
  }
  try {
    // 2. 切换输入法
    await inputMethod.switchInputMethod(currentIme.name);
    console.info('Succeeded in switching inputMethod.');
  } catch (err) {
    console.error(`Failed to switchInputMethod. Code: ${err.code}, message: ${err.message}`);
  }
  const currentSubtype: InputMethodSubtype | undefined = inputMethod.getCurrentInputMethodSubtype();
  if (!currentSubtype) {
    console.error("Failed to get current input subtype");
    return;
  }
  try {
    // 4. 切换输入法子类型
    await inputMethod.switchInputMethod(currentIme.name, currentSubtype.id);
    console.info('Succeeded in switching inputMethod.');
  } catch (err) {
    console.error(`Failed to switchInputMethod. Code: ${err.code}, message: ${err.message}`);
  }
}

switchInputMethodWithSubtype();

```

