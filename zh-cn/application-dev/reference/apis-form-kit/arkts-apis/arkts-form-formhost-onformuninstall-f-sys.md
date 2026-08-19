# onFormUninstall（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## onFormUninstall

```TypeScript
function onFormUninstall(callback: Callback<string>): void
```

Listens to the event of uninstall form. You can use this method to listen to the event of uninstall form.

**起始版本：** 23

<!--Device-formHost-function onFormUninstall(callback: Callback<string>): void--><!--Device-formHost-function onFormUninstall(callback: Callback<string>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;string&gt; | 是 | The callback of formUninstall. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
'use static'

import { formHost } from '@kit.FormKit';

try {
  formHost.onFormUninstall((formId: string) => {
    console.info(`formHost on formUninstall, formId: ${formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

