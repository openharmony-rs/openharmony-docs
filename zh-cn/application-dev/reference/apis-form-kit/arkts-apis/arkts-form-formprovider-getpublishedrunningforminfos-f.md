# getPublishedRunningFormInfos

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getPublishedRunningFormInfos

```TypeScript
function getPublishedRunningFormInfos(): Promise<Array<formInfo.RunningFormInfo>>
```

获取所有已加桌的卡片信息，使用Promise异步回调。适用于卡片管理、批量操作、统计等场景，例如查看应用所有已添加到桌面的卡片信息、批量更新卡片状态等。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getPublishedRunningFormInfos(): Promise<Array<formInfo.RunningFormInfo>>--><!--Device-formProvider-function getPublishedRunningFormInfos(): Promise<Array<formInfo.RunningFormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt; | Promise对象。返回符合条件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.getPublishedRunningFormInfos().then((data: formInfo.RunningFormInfo[]) => {
    console.info(`formProvider getPublishedRunningFormInfos, data: ${JSON.stringify(data)}`);
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

try {
  formProvider.getPublishedRunningFormInfos().then((data: Array<formInfo.RunningFormInfo>) => {
    console.info(`formProvider getPublishedRunningFormInfos`);
  }).catch((error) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

