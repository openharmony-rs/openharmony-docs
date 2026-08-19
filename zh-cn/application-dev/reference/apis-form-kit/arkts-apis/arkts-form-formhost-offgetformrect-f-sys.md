# offGetFormRect（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## offGetFormRect

```TypeScript
function offGetFormRect(callback?: formInfo.GetFormRectInfoCallback): void
```

Cancels listening to the event of get form rect. You can use this method to cancel listening to the event of get form rect.

**起始版本：** 23

<!--Device-formHost-function offGetFormRect(callback?: formInfo.GetFormRectInfoCallback): void--><!--Device-formHost-function offGetFormRect(callback?: formInfo.GetFormRectInfoCallback): void-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | formInfo.GetFormRectInfoCallback | 否 | The callback of get form rect. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

```TypeScript
'use static'

import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let callGetFormRect: formInfo.GetFormRectInfoCallback = (formId: string): Promise<formInfo.Rect> => {
  console.info(`cbGetFormRect a new form`);
  return new Promise<formInfo.Rect>((resolve: (rect: formInfo.Rect) => void, reject: (err: Error) => void): void => {
    console.info(`cbGetFormRect Promise called`);
    let rect1: formInfo.Rect = {
      left: 1.0,
      top: 1.2,
      width: 1.3,
      height: 1.4
    }
  });
}

try {
  formHost.offGetFormRect(callGetFormRect);
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

