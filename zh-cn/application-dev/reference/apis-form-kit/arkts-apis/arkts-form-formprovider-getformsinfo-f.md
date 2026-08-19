# getFormsInfo

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## getFormsInfo

```TypeScript
function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback<Array<formInfo.FormInfo>>): void
```

获取设备上当前应用程序的卡片信息，并筛选符合条件的信息，使用callback异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback<Array<formInfo.FormInfo>>): void--><!--Device-formProvider-function getFormsInfo(filter: formInfo.FormInfoFilter, callback: AsyncCallback<Array<formInfo.FormInfo>>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | formInfo.FormInfoFilter | 是 | 卡片信息过滤器。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;formInfo.FormInfo&gt;&gt; | 是 | 回调函数。返回查询到符合条件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const filter: formInfo.FormInfoFilter = {
  // 获取指定module的卡片信息
  moduleName: 'entry'
};
try {
  formProvider.getFormsInfo(filter, (error, data) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider getFormsInfo, data: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { AsyncCallback } from '@ohos.base';
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const filter: formInfo.FormInfoFilter = {
  moduleName: 'entry'
};
try {
  let callback: AsyncCallback<Array<formInfo.FormInfo>> = (error: BusinessError | null, data: Array<formInfo.FormInfo> | undefined) => {
    if (error?.code != 0) {
      console.error(`callback error, code: ${error?.code}, message: ${error?.message}`);
      return;
    }
    console.info(`formProvider getFormsInfo, item count: ${data?.length}`);
  };
  formProvider.getFormsInfo(filter, callback);
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```


## getFormsInfo

```TypeScript
function getFormsInfo(callback: AsyncCallback<Array<formInfo.FormInfo>>): void
```

获取设备上当前应用程序的卡片信息，使用callback异步回调。适用于卡片管理、调试、统计等场景，例如查看应用所有卡片配置信息、统计卡片数量等。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getFormsInfo(callback: AsyncCallback<Array<formInfo.FormInfo>>): void--><!--Device-formProvider-function getFormsInfo(callback: AsyncCallback<Array<formInfo.FormInfo>>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;formInfo.FormInfo&gt;&gt; | 是 | 回调函数。返回查询到的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formProvider.getFormsInfo((error, data) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider getFormsInfo, data: ${JSON.stringify(data)}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { AsyncCallback } from '@ohos.base';
import { formProvider, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let callback: AsyncCallback<Array<formInfo.FormInfo>> = (error: BusinessError | null, data: Array<formInfo.FormInfo> | undefined) => {
    if (error?.code != 0) {
      console.error(`callback error, code: ${error?.code}, message: ${error?.message}`);
      return;
    }
    console.info(`formProvider getFormsInfo, item count: ${data?.length}`);
  }
  formProvider.getFormsInfo(callback);
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```


## getFormsInfo

```TypeScript
function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise<Array<formInfo.FormInfo>>
```

获取设备上当前应用符合条件的卡片信息，使用Promise异步回调。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise<Array<formInfo.FormInfo>>--><!--Device-formProvider-function getFormsInfo(filter?: formInfo.FormInfoFilter): Promise<Array<formInfo.FormInfo>>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | formInfo.FormInfoFilter | 否 | 卡片信息过滤器，用于筛选指定条件的卡片信息。当需要获取特定模块或特定名称的卡片时传入此参数进行过滤，当需要获取所有卡片信息时可以不传此参 数。不传入时默认为空，返回所有卡片信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt; | Promise对象。返回查询到符合条件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formInfo, formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

const filter: formInfo.FormInfoFilter = {
  // 获取指定module的卡片信息
  moduleName: 'entry'
};
try {
  formProvider.getFormsInfo(filter).then((data: formInfo.FormInfo[]) => {
    console.info(`formProvider getFormsInfo, data: ${JSON.stringify(data)}`);
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

const filter: formInfo.FormInfoFilter = {
  moduleName: 'entry'
};
try {
  formProvider.getFormsInfo(filter).then((data: formInfo.FormInfo[]) => {
    console.info(`formProvider getFormsInfo, item count: ${data?.length}`);
  }).catch((error) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

