# getFormRect

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getFormRect

```TypeScript
function getFormRect(formId: string): Promise<formInfo.Rect>
```

查询卡片位置、尺寸，使用Promise异步回调。适用于需要获取卡片在屏幕上的位置和尺寸信息的场景，例如卡片动效、位置校准、布局计算等。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getFormRect(formId: string): Promise<formInfo.Rect>--><!--Device-formProvider-function getFormRect(formId: string): Promise<formInfo.Rect>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;formInfo.Rect&gt; | Promise对象，返回卡片相对屏幕左上角的位置信息和卡片尺寸信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function getFormRect cannot work correctly due to limited device capabilities. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整

try {
  formProvider.getFormRect(formId).then((data: formInfo.Rect) => {
    console.info(`getFormRect succeed, data: ${JSON.stringify(data)}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整

try {
  formProvider.getFormRect(formId).then((data: formInfo.Rect) => {
    console.info('testTag', `getFormRect succeed, width: ${data.width} height: ${data.height}`);
  }).catch((error) => {
    console.error('testTag', `getFormRect err: code is ${error.code}, message ${error.message}`);
  })
} catch (error) {
  console.error('testTag',
    `getFormRect err: code is ${error.code}, message ${error.message}`);
}
```

