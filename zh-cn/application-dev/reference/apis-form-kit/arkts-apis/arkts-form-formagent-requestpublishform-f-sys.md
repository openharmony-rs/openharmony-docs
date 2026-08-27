# requestPublishForm（系统接口）

## 导入模块

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## requestPublishForm

```TypeScript
function requestPublishForm(want: Want, callback: AsyncCallback<string>): void
```

请求发布一张卡片到使用方，使用callback异步回调。使用方通常为桌面。适用于系统应用需要主动将卡片添加到桌面的场景。

**起始版本：** 11

**需要权限：** ohos.permission.AGENT_REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 发布请求，需包含以下字段。 bundleName: 目标卡片所属应用的bundleName abilityName: 目标卡片所属应用的Ability parameters:    - ohos.extra.param.key.form_dimension: 目标卡片规格，取值原则：1-2x2、2-2x4、3-4x4等，具体规格见卡片配置    - ohos.extra.param.key.form_name: 目标卡片名    - ohos.extra.param.key.module_name: 目标卡片moduleName |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，用于异步返回卡片标识。回调参数：error为错误对象（成功时为null），data为卡片标识（string类型）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified;2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the upper limit.<br>**适用版本：** 26.1.0+ |
| [16501008](../errorcode-form.md#16501008-等待卡片加桌超时) | Waiting for the form addition to the desktop timed out.<br>**适用版本：** 12+ |
| [16501017](../errorcode-form.md#16501017-无空间发布卡片) | There is no space to publish form.<br>**适用版本：** 26.1.0+ |
| [16501018](../errorcode-form.md#16501018-卡片不支持发布) | This form does not support publishing.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
import { formAgent } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  bundleName: 'com.ohos.exampledemo',
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  formAgent.requestPublishForm(want, (error: BusinessError, data: string) => {
    if (error) {
      console.error(`callback error, code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info(`formAgent requestPublishForm, form ID is: ${data}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## requestPublishForm

```TypeScript
function requestPublishForm(want: Want): Promise<string>
```

请求发布一张卡片到使用方，使用Promise异步回调。使用方通常为桌面。适用于系统应用需要主动将卡片添加到桌面的场景。

**起始版本：** 11

**需要权限：** ohos.permission.AGENT_REQUIRE_FORM

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 发布请求，需包含以下字段。 bundleName: 目标卡片所属应用的bundleName abilityName: 目标卡片所属应用的Ability parameters:    - ohos.extra.param.key.form_dimension: 目标卡片规格    - ohos.extra.param.key.form_name: 目标卡片名    - ohos.extra.param.key.module_name: 目标卡片moduleName |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象。返回卡片标识。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16501002](../errorcode-form.md#16501002-卡片数量达到上限) | The number of forms exceeds the upper limit.<br>**适用版本：** 26.1.0+ |
| [16501008](../errorcode-form.md#16501008-等待卡片加桌超时) | Waiting for the form addition to the desktop timed out.<br>**适用版本：** 12+ |
| [16501017](../errorcode-form.md#16501017-无空间发布卡片) | There is no space to publish form.<br>**适用版本：** 26.1.0+ |
| [16501018](../errorcode-form.md#16501018-卡片不支持发布) | This form does not support publishing.<br>**适用版本：** 26.1.0+ |

**示例**

```TypeScript
import { formAgent } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  bundleName: 'com.ohos.exampledemo',
  abilityName: 'FormAbility',
  parameters: {
    'ohos.extra.param.key.form_dimension': 2,
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.module_name': 'entry'
  }
};
try {
  formAgent.requestPublishForm(want).then((data: string) => {
    console.info(`formAgent requestPublishForm success, form ID is : ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
