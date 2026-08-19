# onGetLiveFormStatus（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## onGetLiveFormStatus

```TypeScript
function onGetLiveFormStatus(callback: formInfo.GetLiveFormStatusCallback): void
```

Listens to the event of get live form status.

**起始版本：** 23

<!--Device-formHost-function onGetLiveFormStatus(callback: formInfo.GetLiveFormStatusCallback): void--><!--Device-formHost-function onGetLiveFormStatus(callback: formInfo.GetLiveFormStatusCallback): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | formInfo.GetLiveFormStatusCallback | 是 | The callback of get live form status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
'use static'

import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.onGetLiveFormStatus((): Record<string, string> => {
    // 卡片使用方需要对查询请求进行处理，计算并返回状态信息
    return { "status": "active" };
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

