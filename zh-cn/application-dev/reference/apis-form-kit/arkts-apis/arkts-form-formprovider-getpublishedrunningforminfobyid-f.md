# getPublishedRunningFormInfoById

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getPublishedRunningFormInfoById

```TypeScript
function getPublishedRunningFormInfoById(formId: string): Promise<formInfo.RunningFormInfo>
```

获取当前应用已加桌的指定卡片信息，使用Promise异步回调。适用于卡片管理、调试等场景，例如查看指定卡片的位置信息和尺寸信息。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getPublishedRunningFormInfoById(formId: string): Promise<formInfo.RunningFormInfo>--><!--Device-formProvider-function getPublishedRunningFormInfoById(formId: string): Promise<formInfo.RunningFormInfo>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;formInfo.RunningFormInfo&gt; | Promise对象。返回符合条件的卡片信息，包括卡片名称、尺寸等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const formId: string = '388344236';

try {
  formProvider.getPublishedRunningFormInfoById(formId).then((data: formInfo.RunningFormInfo) => {
    console.info(`formProvider getPublishedRunningFormInfoById, data: ${JSON.stringify(data)}`);
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

const formId: string = '388344236';

try {
  formProvider.getPublishedRunningFormInfoById(formId).then((data: formInfo.RunningFormInfo) => {
    console.info(`formProvider getPublishedRunningFormInfoById, formId: ${data.formId}`);
  }).catch((error) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

