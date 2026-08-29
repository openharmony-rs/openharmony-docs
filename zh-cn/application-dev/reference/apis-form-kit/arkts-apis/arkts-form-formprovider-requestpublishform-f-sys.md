# requestPublishForm（系统接口）

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## requestPublishForm

```TypeScript
function requestPublishForm(
    want: Want,
    formBindingData: formBindingData.FormBindingData,
    callback: AsyncCallback<string>
  ): void
```

请求发布一张卡片到使用方。使用方通常为桌面，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 发布请求，需包含以下字段。 abilityName: 目标卡片ability parameters: 'ohos.extra.param.key.form_dimension''ohos.extra.param.key.form_name''ohos.extra.param.key.module_name' |
| formBindingData | formBindingData.FormBindingData | 是 | 创建卡片的数据。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回卡片标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the upper limit.<br>**适用版本：** 26.1.0+ |
| [16501008](../errorcode-form.md#16501008-等待卡片加桌超时) | Waiting for the form addition to the desktop timed out.<br>**适用版本：** 26.1.0+ |
| [16501017](../errorcode-form.md#16501017-无空间发布卡片) | There is no space to publish form.<br>**适用版本：** 26.1.0+ |
| [16501018](../errorcode-form.md#16501018-卡片不支持发布) | This form does not support publishing.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
import { formBindingData, formProvider } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  let param: Record<string, string> = {
    'temperature': '22c',
    'time': '22:00'
  }
  let obj: formBindingData.FormBindingData = formBindingData.createFormBindingData(param);
  formProvider.requestPublishForm(want, obj, (error: BusinessError, data: string) => {
    if (error) {
      console.error(`callback error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
      return;
    }
    console.info(`formProvider requestPublishForm, form ID is: ${data}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## requestPublishForm

```TypeScript
function requestPublishForm(want: Want, callback: AsyncCallback<string>): void
```

请求发布一张卡片到使用方。使用方通常为桌面，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 发布请求，需包含以下字段。 abilityName: 目标卡片ability parameters: 'ohos.extra.param.key.form_dimension''ohos.extra.param.key.form_name''ohos.extra.param.key.module_name' |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回卡片标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the upper limit.<br>**适用版本：** 26.1.0+ |
| [16501008](../errorcode-form.md#16501008-等待卡片加桌超时) | Waiting for the form addition to the desktop timed out.<br>**适用版本：** 26.1.0+ |
| [16501017](../errorcode-form.md#16501017-无空间发布卡片) | There is no space to publish form.<br>**适用版本：** 26.1.0+ |
| [16501018](../errorcode-form.md#16501018-卡片不支持发布) | This form does not support publishing.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
import { formProvider } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  formProvider.requestPublishForm(want, (error: BusinessError, data: string) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formProvider requestPublishForm, form ID is: ${data}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## requestPublishForm

```TypeScript
function requestPublishForm(want: Want, formBindingData?: formBindingData.FormBindingData): Promise<string>
```

请求发布一张卡片到使用方。使用方通常为桌面，使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 发布请求，需包含以下字段。 abilityName: 目标卡片ability parameters: 'ohos.extra.param.key.form_dimension''ohos.extra.param.key.form_name''ohos.extra.param.key.module_name' |
| formBindingData | formBindingData.FormBindingData | 否 | 创建卡片的数据，默认为空，不提供创建卡片数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;string&gt; | Promise对象。返回卡片标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the upper limit.<br>**适用版本：** 26.1.0+ |
| [16501008](../errorcode-form.md#16501008-等待卡片加桌超时) | Waiting for the form addition to the desktop timed out.<br>**适用版本：** 26.1.0+ |
| [16501017](../errorcode-form.md#16501017-无空间发布卡片) | There is no space to publish form.<br>**适用版本：** 26.1.0+ |
| [16501018](../errorcode-form.md#16501018-卡片不支持发布) | This form does not support publishing.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
import { formProvider } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  formProvider.requestPublishForm(want).then((data: string) => {
    console.info(`formProvider requestPublishForm success, form ID is : ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
