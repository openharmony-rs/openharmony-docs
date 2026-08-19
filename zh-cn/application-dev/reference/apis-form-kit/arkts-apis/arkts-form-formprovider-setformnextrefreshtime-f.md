# setFormNextRefreshTime

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## setFormNextRefreshTime

```TypeScript
function setFormNextRefreshTime(formId: string, minute: int, callback: AsyncCallback<void>): void
```

设置指定卡片的下一次刷新时间，使用callback异步回调。适用于需要精确控制卡片刷新时机的场景，例如定时任务等。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: int, callback: AsyncCallback<void>): void--><!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| minute | int | 是 | 指定卡片多久之后刷新，取值范围：大于等于5，单位：min。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。设置结果的回调，成功时error为undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the maximum allowed. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整
try {
  formProvider.setFormNextRefreshTime(formId, 5, (error: BusinessError) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider setFormNextRefreshTime success`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
'use static'

import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';  // 表示卡片formId，根据实际formId调整
let minute: int = 5;
try {
  formProvider.setFormNextRefreshTime(formId, minute, (error,data) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('formProvider setFormNextRefreshTime success');
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```


## setFormNextRefreshTime

```TypeScript
function setFormNextRefreshTime(formId: string, minute: int): Promise<void>
```

设置指定卡片的下一次刷新时间，使用Promise异步回调。适用于需要精确控制卡片刷新时机的场景，例如定时任务等。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: int): Promise<void>--><!--Device-formProvider-function setFormNextRefreshTime(formId: string, minute: int): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |
| minute | int | 是 | 指定卡片多久之后刷新，取值范围：大于等于5，单位：min。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the maximum allowed. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整
try {
  formProvider.setFormNextRefreshTime(formId, 5).then(() => {
    console.info(`formProvider setFormNextRefreshTime success`);
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

import { formProvider } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288'; // 表示卡片formId，根据实际formId调整
let minute: int = 3;
try {
  formProvider.setFormNextRefreshTime(formId, minute).then(() => {
    console.info('testTag', `FormProvider setFormNextRefreshTime success`);
  }).catch((error) => {
    console.error('testTag', `FormProvider promise error, code: ${error.code}, message: ${error.message}`);
  });
  console.info('testTag', 'FormProvider setFormNextRefreshTime register success');
} catch (error) {
  console.error('testTag', `FormProvider catch error, code: ${error.code}, message: ${error.message}`);
}
```

