# getFormIdsByFormLocation（系统接口）

## 导入模块

```TypeScript
import { formHost } from '@kit.FormKit';
```

## getFormIdsByFormLocation

```TypeScript
function getFormIdsByFormLocation(location: formInfo.FormLocation): Promise<Array<string>>
```

获取设备上指定卡片位置的卡片标识列表。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-formHost-function getFormIdsByFormLocation(location: formInfo.FormLocation): Promise<Array<string>>--><!--Device-formHost-function getFormIdsByFormLocation(location: formInfo.FormLocation): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| location | formInfo.FormLocation | 是 | 卡片位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象。返回查询到的卡片标识列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501016](../errorcode-form.md#16501016-卡片位置信息无效) | The location of the widget is invalid. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permissions denied. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.getFormIdsByFormLocation(formInfo.FormLocation.DESKTOP).then((formIds: Array<string>) => {
    console.info('formHost getFormIdsByFormLocation success.');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { formHost, formInfo } from '@kit.FormKit';

try {
  formHost.getFormIdsByFormLocation(formInfo.FormLocation.DESKTOP).then((formIds: Array<string>) => {
    console.info('formHost getFormIdsByFormLocation success.');
  }).catch((error) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

