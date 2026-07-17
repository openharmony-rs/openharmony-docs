# switchInputMethod

## 导入模块

```TypeScript
import { inputMethod } from '@kit.IMEKit';
```

## switchInputMethod

```TypeScript
function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback<boolean>): void
```

切换输入法，使用callback异步回调。

**含义/功能**：将当前输入法切换为指定的目标输入法。

**使用场景：**当前输入法应用需要切换到另一个输入法时使用（如用户在输入法设置中选择了新的输入法）。

**使用后效果**：成功时系统将当前输入法切换为目标输入法，目标输入法成为新的当前输入法；失败时当前输入法不变。

**异步返回方式**：使用callback异步回调。成功时err为undefined，data为true；失败时返回BusinessError对象。

**起始版本：** 9

**需要权限：** 
- API版本9 - 10：ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback<boolean>): void--><!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | 目标输入法。<br/>**使用场景：**指定要切换到的目标输入法，通过name和id唯一确定。<br/>**说明：**只需填写name和id字段即可唯一指定一个输入法，无需填写label、icon等可选字段。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 回调函数。当输入法切换成功，err为undefined，data为true；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails.<br>**适用版本：** 9 - 10 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-配置持久化失败) | configuration persistence error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
inputMethod.switchInputMethod(currentIme, (err: BusinessError, result: boolean) => {
  if (err) {
    console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
    return;
  }
  if (result) {
    console.info('Succeeded in switching input method.');
  } else {
    console.error('Failed to switch input method.');
  }
});

```


## switchInputMethod

```TypeScript
function switchInputMethod(target: InputMethodProperty): Promise<boolean>
```

切换输入法，使用promise异步回调。

**含义/功能**：将当前输入法切换为指定的目标输入法。

**使用场景：**当前输入法应用需要切换到另一个输入法时使用。

**使用后效果**：成功时系统将当前输入法切换为目标输入法；失败时当前输入法不变。

**异步返回方式**：使用Promise异步回调。成功时返回true，失败时返回BusinessError对象。

**起始版本：** 9

**需要权限：** 
- API版本9 - 10：ohos.permission.CONNECT_IME_ABILITY

<!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty): Promise<boolean>--><!--Device-inputMethod-function switchInputMethod(target: InputMethodProperty): Promise<boolean>-End-->

**系统能力：** SystemCapability.MiscServices.InputMethodFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | [InputMethodProperty](arkts-ime-inputmethod-inputmethodproperty-i.md) | 是 | 目标输入法。<br/>**使用场景：**指定要切换到的目标输入法，通过name和id唯一确定。<br/>**说明：**只需填写name和id字段即可唯一指定一个输入法。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回true表示切换输入法成功，返回false表示切换输入法失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permissions check fails.<br>**适用版本：** 9 - 10 |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [12800005](../errorcode-inputmethod-framework.md#12800005-配置持久化失败) | configuration persistence error. |
| [12800008](../errorcode-inputmethod-framework.md#12800008-输入法管理服务异常) | input method manager service error. Possible cause:a system error, such as null pointer, IPC exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let currentIme: inputMethod.InputMethodProperty = inputMethod.getCurrentInputMethod();
inputMethod.switchInputMethod(currentIme).then((result: boolean) => {
  if (result) {
    console.info('Succeeded in switching input method.');
  } else {
    console.error('Failed to switch input method.');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to switchInputMethod, code: ${err.code}, message: ${err.message}`);
});

```

