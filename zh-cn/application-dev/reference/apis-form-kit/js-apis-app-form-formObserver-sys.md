# @ohos.app.form.formObserver (formObserver)(系统接口)

formObserver模块提供了卡片监听方相关接口的能力，包括对同一用户下安装的卡片新增、删除、可见性变化事件的订阅和取消订阅，获取正在运行的卡片信息等。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口均为系统接口。

## 导入模块

```ts
import { formObserver } from '@kit.FormKit';
```

## on('formAdd')

 on(type: 'formAdd', observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片新增事件。使用callback异步回调，返回当前新增卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| type | string | 是   | 填写'formAdd'，表示卡片新增事件。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是 | 回调函数。返回当前新增卡片的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.on('formAdd', callback);
```

## onFormAdd<sup>23+</sup>

 onFormAdd(observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片新增事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                               |
| ---------------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回当前新增卡片的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest019 observerCallback success`);
  };
  formObserver.onFormAdd(observerCallback);
  console.info('testTag', 'formObserverStaticTest019 formObserver on success');
  formObserver.offFormAdd(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest019 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest019 catch error, code: ${code}, message: ${message})`);
}
```

## on('formAdd')

 on(type: 'formAdd', hostBundleName: string, observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片新增事件。使用callback异步回调，返回指定卡片使用方应用新增卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| type | string | 是   | 填写'formAdd'，表示卡片新增事件。 |
| hostBundleName | string | 是 | 指定订阅卡片使用方包的bundleName。缺省则订阅所有卡片使用方的卡片新增事件。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是 | 回调函数。返回指定卡片使用方应用新增卡片的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.on('formAdd', bundleName, callback);
```

## onFormAdd<sup>23+</sup>

onFormAdd(hostBundleName: string, observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片新增事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定订阅卡片使用方包的bundleName。缺省则订阅所有卡片使用方的卡片新增事件。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回指定卡片使用方应用新增卡片的信息。             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest020 observerCallback success`);
  };
  formObserver.onFormAdd(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest020 formObserver on success');
  formObserver.offFormAdd(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest020 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest020 catch error, code: ${code}, message: ${message})`);
}
```

## off('formAdd')

 off(type: "formAdd", hostBundleName?: string, observerCallback?: Callback&lt;formInfo.RunningFormInfo&gt;): void

取消订阅卡片新增事件。使用callback异步回调，返回当前新增卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| type | string | 是   | 填写'formAdd'，表示卡片新增事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。<br> 填写该参数时，与注册时填写bundleName的on接口对应。<br> 缺省则订阅所有卡片使用方的卡片删除事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否 | 回调函数。返回当前新增卡片信息。缺省时，表示注销对应已注册事件回调。<br> 需与对应on('formAdd')的callback一致。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.off('formAdd', bundleName, callback);

```
> **说明：**
>
> - on('formAdd', callback)与off('formAdd', callback)相对应；
> - on('formAdd', bundleName, callback)与off('formAdd', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offFormAdd<sup>23+</sup>

offFormAdd(hostBundleName?: string, observerCallback?: Callback\<formInfo.RunningFormInfo\>): void

取消订阅卡片新增事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定订阅卡片使用方包的bundleName。<br> 填写该参数时，与注册时填写bundleName的on接口对应。<br> 缺省则订阅所有卡片使用方的卡片删除事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回当前新增卡片信息。缺省时，表示注销对应已注册事件回调。<br> 需与对应onFormAdd的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest019 observerCallback success`);
  };
  formObserver.onFormAdd(observerCallback);
  console.info('testTag', 'formObserverStaticTest019 formObserver on success');
  formObserver.offFormAdd(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest019 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest019 catch error, code: ${code}, message: ${message})`);
}
```

> **说明：**
>
> - onFormAdd(callback)与offFormAdd(callback)相对应；
> - onFormAdd(bundleName, callback)与offFormAdd(bundleName, callback)相对应；
> - 订阅（onFormAdd）只能由自己对应的取消订阅接口（offFormAdd）取消。

## on('formRemove')

 on(type: 'formRemove', observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片删除事件。使用callback异步回调，返回当前删除卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| type | string | 是   | 填写'formRemove'，表示卡片删除事件。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是 | 回调函数。返回当前删除卡片的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`form deleted, formId: ${data.formId}`);
}

formObserver.on('formRemove', callback);
```

## onFormRemove<sup>23+</sup>

 onFormRemove(observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片删除事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                               |
| ---------------- | ------------------------------------------------------------ | ---- | ---------------------------------- |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回当前删除卡片的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest017 observerCallback success`);
  };
  formObserver.onFormRemove(observerCallback);
  console.info('testTag', 'formObserverStaticTest017 formObserver on success');
  formObserver.offFormRemove(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest017 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest017 catch error, code: ${code}, message: ${message})`);
}
```

## on('formRemove')

 on(type: 'formRemove', hostBundleName: string, observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片删除事件。使用callback异步回调，返回指定卡片使用方应用被删除卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| type | string | 是   | 填写'formRemove'，表示卡片删除事件。 |
| hostBundleName | string | 是 | 指定订阅卡片使用方包的bundleName。缺省则订阅所有卡片使用方的卡片删除事件。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是 | 回调函数。返回指定卡片使用方应用被删除卡片的信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`form deleted, formId: ${data.formId}`);
}

formObserver.on('formRemove', bundleName, callback);
```

## onFormRemove<sup>23+</sup>

onFormRemove(hostBundleName: string, observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片删除事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定订阅卡片使用方包的bundleName。缺省则订阅所有卡片使用方的卡片删除事件。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回指定卡片使用方应用被删除卡片的信息。           |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest018 observerCallback success`);
  };
  formObserver.onFormRemove(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest018 formObserver on success');
  formObserver.offFormRemove(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest018 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest018 catch error, code: ${code}, message: ${message})`);
}
```

## off('formRemove')

off(type: "formRemove", hostBundleName?: string, observerCallback?: Callback&lt;formInfo.RunningFormInfo&gt;): void

取消订阅卡片删除事件。使用callback异步回调，返回当前删除卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| type | string | 是   | 填写'formRemove'，表示卡片删除事件。 |
| hostBundleName | string | 否 | 指定订阅卡片使用方包的bundleName。<br> 填写该参数时，与注册时填写bundleName的on接口对应。<br> 缺省则订阅所有卡片使用方的卡片删除事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否 | 回调函数。返回当前删除卡片的信息。缺省时，表示注销对应已注册事件回调。<br> 需与对应on('formRemove')的callback一致。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.off('formRemove', bundleName, callback);
```
> **说明：**
>
> - on('formRemove', callback)与off('formRemove', callback)相对应；
> - on('formRemove', bundleName, callback)与off('formRemove', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offFormRemove<sup>23+</sup>

offFormRemove(hostBundleName?: string, observerCallback?: Callback\<formInfo.RunningFormInfo\>): void

取消订阅卡片删除事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定订阅卡片使用方包的bundleName。<br> 填写该参数时，与注册时填写bundleName的on接口对应。<br> 缺省则订阅所有卡片使用方的卡片删除事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回当前删除卡片的信息。缺省时，表示注销对应已注册事件回调。<br> 需与对应onFormRemove的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest017 observerCallback success`);
  };
  formObserver.onFormRemove(observerCallback);
  console.info('testTag', 'formObserverStaticTest017 formObserver on success');
  formObserver.offFormRemove(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest017 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest017 catch error, code: ${code}, message: ${message})`);
}
```

> **说明：**
>
> - onFormRemove(callback)与offFormRemove(callback)相对应；
> - onFormRemove(bundleName, callback)与offFormRemove( bundleName, callback)相对应；
> - 订阅（onFormRemove）只能由自己对应的取消订阅接口（offFormRemove）取消。

## on('notifyVisible')

on(type: 'notifyVisible', observerCallback: Callback&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;): void

订阅通知卡片可见的事件。使用callback异步回调。

触发通知卡片可见场景为：调用[notifyVisibleForms](js-apis-app-form-formHost-sys.md#notifyvisibleforms)接口通知对应卡片可见性变更为可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | 是   | 仅允许填写'notifyVisible'，表示订阅通知卡片可见的事件。      |
| observerCallback   | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅该事件的卡片信息列表。            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo[]) => {
  console.info(`form change visibility, formId: ${data.formId}`);
}

formObserver.on('notifyVisible', callback);

```

## onNotifyVisible<sup>23+</sup>

onNotifyVisible(observerCallback: Callback\<Array\<formInfo.RunningFormInfo\>\>): void

订阅通知卡片可见的事件。使用callback异步回调。

触发通知卡片可见场景为：调用[notifyVisibleForms](js-apis-app-form-formHost-sys.md#notifyvisibleforms)接口通知对应卡片可见性变更为可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                     |
| ---------------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| observerCallback | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅该事件的卡片信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let observerCallback = (data: Array<formInfo.RunningFormInfo>) => {
    console.info('testTag', `formObserverStaticTest022 observerCallback success`);
  };
  formObserver.onNotifyVisible(observerCallback);
  console.info('testTag', 'formObserverStaticTest022 formObserver on success');
  formObserver.offNotifyVisible(undefined, observerCallback);
  console.info('testTag', 'formObserverStaticTest022 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest022 catch error, code: ${code}, message: ${message})`);
}
```

## on('notifyVisible')

on(type: 'notifyVisible', hostBundleName: string, observerCallback: Callback&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;): void

订阅通知卡片可见的事件。使用callback异步回调。

触发通知卡片可见场景为：调用[notifyVisibleForms](js-apis-app-form-formHost-sys.md#notifyvisibleforms)接口通知对应卡片可见性变更为可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | 是   | 仅允许填写'notifyVisible'，表示订阅通知卡片可见的事件。      |
| hostBundleName | string                                                       | 是   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。 |
| observerCallback   | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅该事件的卡片信息列表。            |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  console.info(`form change visibility, item count: ${data.length}`);
}

formObserver.on('notifyVisible', bundleName, callback);
```

## onNotifyVisible<sup>23+</sup>

onNotifyVisible(hostBundleName: string, observerCallback: Callback\<Array\<formInfo.RunningFormInfo\>\>): void

订阅通知卡片可见的事件。使用callback异步回调。

触发通知卡片可见场景为：调用[notifyVisibleForms](js-apis-app-form-formHost-sys.md#notifyvisibleforms)接口通知对应卡片可见性变更为可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。 |
| observerCallback | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅该事件的卡片信息列表。                     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: Array<formInfo.RunningFormInfo>) => {
    console.info('testTag', `formObserverStaticTest021 observerCallback success`);
  };
  formObserver.onNotifyVisible(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest021 formObserver on success');
  formObserver.offNotifyVisible(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest021 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest021 catch error, code: ${code}, message: ${message})`);
}
```

## off('notifyVisible')

off(type: "notifyVisible", hostBundleName?: string, observerCallback?: Callback&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;): void

取消订阅通知卡片可见的事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | 是   | 仅允许填写'notifyVisible'，表示取消订阅通知卡片为可见的事件。 |
| hostBundleName | string                                                       | 否   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。<br> 填写该参数时，与注册时填写bundleName的on接口对应。 |
| observerCallback   | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 否   | 回调函数。返回取消订阅该事件的卡片信息列表。缺省时，表示注销对应已注册订阅的回调。<br> 需与对应on('notifyVisible')的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  console.info(`form change visibility, item count: ${data.length}`);
}

formObserver.off('notifyVisible', bundleName, callback);
```

> **说明：**
>
> - on('notifyVisible', callback)与off('notifyVisible', callback)相对应；
> - on('notifyVisible', bundleName, callback)与off('notifyVisible', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offNotifyVisible<sup>23+</sup>

offNotifyVisible(hostBundleName?: string, observerCallback?: Callback\<Array\<formInfo.RunningFormInfo\>\>): void

取消订阅通知卡片可见的事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。<br> 填写该参数时，与注册时填写bundleName的on接口对应。 |
| observerCallback | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 否   | 回调函数。返回取消订阅该事件的卡片信息列表。缺省时，表示注销对应已注册订阅的回调。<br> 需与对应onNotifyVisible的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: Array<formInfo.RunningFormInfo>) => {
    console.info('testTag', `formObserverStaticTest021 observerCallback success`);
  };
  formObserver.onNotifyVisible(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest021 formObserver on success');
  formObserver.offNotifyVisible(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest021 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest021 catch error, code: ${code}, message: ${message})`);
}
```

> **说明：**
>
> - onNotifyVisible(callback)与offNotifyVisible(callback)相对应；
> - onNotifyVisible(bundleName, callback)与offNotifyVisible( bundleName, callback)相对应；
> - 订阅（onNotifyVisible）只能由自己对应的取消订阅接口（offNotifyVisible）取消。

## on('notifyInvisible')

 on(type: 'notifyInvisible', observerCallback: Callback&lt;Array&lt;formInfo.RunningFormInfo&gt;>): void

订阅通知卡片不可见的事件。使用callback异步回调。

触发通知卡片不可见场景为：调用[notifyInvisibleForms](js-apis-app-form-formHost-sys.md#notifyinvisibleforms)接口通知对应卡片可见性变更为不可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | 是   | 仅允许填写'notifyInvisible'，表示订阅卡片不可见的事件。      |
| observerCallback   | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅通知卡片不可见的卡片信息列表。          |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo[]) => {
  console.info(`form change invisibility, item count: ${data.length}`);
}

formObserver.on('notifyInvisible', callback);
```

## onNotifyInvisible<sup>23+</sup>

 onNotifyInvisible(observerCallback: Callback\<Array\<formInfo.RunningFormInfo\>\>): void

订阅通知卡片不可见的事件。使用callback异步回调。

触发通知卡片不可见场景为：调用[notifyInvisibleForms](js-apis-app-form-formHost-sys.md#notifyinvisibleforms)接口通知对应卡片可见性变更为不可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                             |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| observerCallback | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅通知卡片不可见的卡片信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: Array<formInfo.RunningFormInfo>) => {
    console.info('testTag', `formObserverStaticTest023 observerCallback success`);
  };
  formObserver.onNotifyInvisible(observerCallback);
  console.info('testTag', 'formObserverStaticTest023 formObserver on success');
  formObserver.offNotifyInvisible(undefined, observerCallback);
  console.info('testTag', 'formObserverStaticTest023 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest023 catch error, code: ${code}, message: ${message})`);
}
```

## on('notifyInvisible')

on(type: 'notifyInvisible', hostBundleName: string, observerCallback: Callback&lt;Array&lt;formInfo.RunningFormInfo&gt;>): void

订阅通知卡片不可见的事件。使用callback异步回调。

触发通知卡片不可见场景为：调用[notifyInvisibleForms](js-apis-app-form-formHost-sys.md#notifyinvisibleforms)接口通知对应卡片可见性变更为不可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | 是   | 仅允许填写'notifyInvisible'，表示订阅卡片不可见的事件。      |
| hostBundleName | string                                                       | 是   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。 |
| observerCallback   | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅通知卡片不可见的卡片信息列表。          |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  console.info(`form change invisibility, item count: ${data.length}`);
}

formObserver.on('notifyInvisible', bundleName, callback);
```

## onNotifyInvisible<sup>23+</sup>

onNotifyInvisible(hostBundleName: string, observerCallback: Callback\<Array\<formInfo.RunningFormInfo\>\>): void

订阅通知卡片不可见的事件。使用callback异步回调。

触发通知卡片不可见场景为：调用[notifyInvisibleForms](js-apis-app-form-formHost-sys.md#notifyinvisibleforms)接口通知对应卡片可见性变更为不可见状态。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。 |
| observerCallback | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是   | 回调函数。返回订阅通知卡片不可见的卡片信息列表。             |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: Array<formInfo.RunningFormInfo>) => {
    console.info('testTag', `formObserverStaticTest024 observerCallback success`);
  };
  formObserver.onNotifyInvisible(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest024 formObserver on success');
  formObserver.offNotifyInvisible(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest024 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest024 catch error, code: ${code}, message: ${message})`);
}
```

## off('notifyInvisible')

off(type: "notifyInvisible", hostBundleName?: string, observerCallback?: Callback&lt;Array&lt;formInfo.RunningFormInfo>&gt;): void

取消订阅通知卡片不可见事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 10

**参数：**

| 参数名     | 类型                                                         | 必填 | 说明                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type       | string                                                       | 是   | 仅允许填写'notifyInvisible'，表示卡片可见性变更为不可见。    |
| hostBundleName | string                                                       | 否   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。<br> 填写该参数时，与注册时填写bundleName的on接口对应。<br>  |
| observerCallback   | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 否   | 回调函数。返回取消订阅通知卡片不可见的卡片信息列表。缺省时，表示注销对应已注册事件回调。<br/> 需与对应on('notifyInvisible')的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  console.info(`form change invisibility, item count: ${data.length}`);
}

formObserver.off('notifyInvisible', bundleName, callback);
```

> **说明：**
>
> - on('notifyInvisible', callback)与off('notifyInvisible', callback)相对应；
> - on('notifyInvisible', bundleName, callback)与off('notifyInvisible', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offNotifyInvisible<sup>23+</sup>

offNotifyInvisible(hostBundleName?: string, observerCallback?: Callback\<Array\<formInfo.RunningFormInfo\>\>): void

取消订阅通知卡片不可见事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。<br> 填写该参数时，与注册时填写bundleName的on接口对应。<br> |
| observerCallback | Callback &lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 否   | 回调函数。返回取消订阅通知卡片不可见的卡片信息列表。缺省时，表示注销对应已注册事件回调。<br/> 需与对应onNotifyInvisible的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: Array<formInfo.RunningFormInfo>) => {
    console.info('testTag', `formObserverStaticTest023 observerCallback success`);
  };
  formObserver.onNotifyInvisible(observerCallback);
  console.info('testTag', 'formObserverStaticTest023 formObserver on success');
  formObserver.offNotifyInvisible(undefined, observerCallback);
  console.info('testTag', 'formObserverStaticTest023 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest023 catch error, code: ${code}, message: ${message})`);
}
```

> **说明：**
>
> - onNotifyInvisible(callback)与offNotifyInvisible(callback)相对应；
> - onNotifyInvisible(bundleName, callback)与offNotifyInvisible(bundleName, callback)相对应；
> - 订阅（onNotifyInvisible）只能由自己对应的取消订阅接口（offNotifyInvisible）取消。

## getRunningFormInfos

getRunningFormInfos(callback: AsyncCallback&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;, hostBundleName?: string): void

获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| callback | AsyncCallback&lt;Array&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是 | 回调函数。获取设备上正在运行的所有非临时卡片信息。当前卡片信息成功，error为undefined，data为查询到的卡片信息。|
| hostBundleName | string | 否 |  指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos((error: BusinessError, data: formInfo.RunningFormInfo[]) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfos, item count: ${data.length}`);
    }
  }, 'com.example.ohos.formjsdemo');
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { AsyncCallback } from '@ohos.base';
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let callback: AsyncCallback<Array<formInfo.RunningFormInfo>> = (error: BusinessError | null, data: Array<formInfo.RunningFormInfo> | undefined) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfos, item count: ${data?.length}`);
    }
  };
  formObserver.getRunningFormInfos(callback, 'com.example.ohos.formjsdemo');
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## getRunningFormInfos<sup>11+</sup>

getRunningFormInfos(callback: AsyncCallback&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;, isUnusedIncluded: boolean, hostBundleName?: string): void

获取设备上正在运行的所有非临时卡片信息。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| callback | AsyncCallback&lt;Array&lt;formInfo.[RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是 |  回调函数。获取设备上正在运行的所有非临时卡片信息。当获取成功时，回调中的error为undefined，data为查询到的卡片信息。|
| isUnusedIncluded | boolean | 是 |  表示是否包含未使用的卡片。<br>true: 表示包含未使用的卡片。<br>false: 表示不包含未使用的卡片。|
| hostBundleName | string | 否 |  指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos((error: BusinessError, data: formInfo.RunningFormInfo[]) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfos, item count: ${data.length}`);
    }
  }, true, 'com.example.ohos.formjsdemo');
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos((error: BusinessError | null, data: formInfo.RunningFormInfo[] | undefined) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      if (data !== undefined) {
        for (let runningFormInfo of data) {
          console.info(`formObserver getRunningFormInfos, hostBundleName : ${runningFormInfo.hostBundleName}`);
        }
      }
    }
  }, true, 'com.example.ohos.formjsdemo');
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## getRunningFormInfos

getRunningFormInfos(hostBundleName?: string):  Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;

获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| hostBundleName | string | 否 |  指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**返回值：**

| 类型                                                         | 说明                                |
| :----------------------------------------------------------- | :---------------------------------- |
| Promise&lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | Promise对象。返回设备上正在运行的所有非临时卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos('com.example.ohos.formjsdemo').then((data: formInfo.RunningFormInfo[]) => {
    console.info(`formObserver getRunningFormInfos, item count: ${data.length}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos('com.example.ohos.formjsdemo').then((data: formInfo.RunningFormInfo[]) => {
    for (let runningFormInfo of data) {
      console.info(`formObserver getRunningFormInfos, hostBundleName : ${runningFormInfo.hostBundleName}`);
    }
  }).catch((err) => {
    let error = err as BusinessError;
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## getRunningFormInfos<sup>11+</sup>

getRunningFormInfos(isUnusedIncluded: boolean, hostBundleName?: string):  Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;

获取设备上正在运行的所有非临时卡片信息。使用Promise异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明    |
| ------ | ------ | ---- | ------- |
| isUnusedIncluded | boolean | 是 |  表示是否包含未使用的卡片。<br>true: 表示包含未使用的卡片。<br>false: 表示不包含未使用的卡片。 |
| hostBundleName | string | 否 |  指定要查询的卡片使用方名称，指定后会仅返回该卡片使用方下正在运行的非临时卡片信息。 <br> 缺省时，返回设备上所有正在运行的非临时卡片信息。 |

**返回值：**

| 类型                                                         | 说明                                |
| :----------------------------------------------------------- | :---------------------------------- |
| Promise&lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | Promise对象。返回设备上正在运行的所有非临时卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos(true, 'com.example.ohos.formjsdemo').then((data: formInfo.RunningFormInfo[]) => {
    console.info(`formObserver getRunningFormInfos, item count: ${data.length}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formObserver.getRunningFormInfos(true, 'com.example.ohos.formjsdemo')
    .then((data: Array<formInfo.RunningFormInfo>) => {
      console.info(`formObserver getRunningFormInfos, item count: ${data?.length}`);
    })
    .catch((error) => {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## getRunningFormInfosByFilter

getRunningFormInfosByFilter(formProviderFilter: formInfo.FormProviderFilter): Promise&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;

根据提供方信息查询已添加的卡片信息列表。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填 | 说明                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formProviderFilter     | [formInfo.FormProviderFilter](js-apis-app-form-formInfo-sys.md#formproviderfilter10) | 是   | 卡片提供方应用信息。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | Promise对象。返回已添加的卡片信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000  | An internal functional error occurred. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formInstanceFilter: formInfo.FormProviderFilter = {
  bundleName: "com.example.formprovide",
  abilityName: "EntryFormAbility",
  formName: "widget",
  moduleName: "entry"
}
try {
  formObserver.getRunningFormInfosByFilter(formInstanceFilter).then((data: formInfo.RunningFormInfo[]) => {
    console.info(`formObserver getRunningFormInfosByFilter success, item count: ${data.length}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let formProviderFilter: formInfo.FormProviderFilter = {
    bundleName: 'com.example.demoForm',
    formName: 'widget'
  };
  formObserver.getRunningFormInfosByFilter(formProviderFilter)
    .then((data: Array<formInfo.RunningFormInfo> | undefined) => {
      console.info('testTag', `formObserverStaticTest009 promise success`);
    }).catch((error: Error) => {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    hilog.error(DOMAIN, TAG, `formObserverStaticTest009 promise error, code: ${code} message: ${message}`);
  });
} catch (error: BusinessError) {
  hilog.error(DOMAIN, TAG, 'formObserverStaticTest009 catch error');
}
```

## getRunningFormInfosByFilter

getRunningFormInfosByFilter(formProviderFilter: formInfo.FormProviderFilter, callback: AsyncCallback&lt;Array&lt;formInfo.RunningFormInfo&gt;&gt;): void

根据提供方信息查询已添加的卡片信息列表。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填 | 说明                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formProviderFilter     | [formInfo.FormProviderFilter](js-apis-app-form-formInfo-sys.md#formproviderfilter10) | 是   | 卡片提供方应用信息。 |
| callback | AsyncCallback&lt;Array&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt;&gt; | 是 | 回调函数。返回已添加的卡片信息列表。error为undefined，data为查询到的使用方列表信息；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000  | An internal functional error occurred. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formInstanceFilter: formInfo.FormProviderFilter = {
  bundleName: "com.example.formprovide",
  abilityName: "EntryFormAbility",
  formName: "widget",
  moduleName: "entry"
}
try {
  formObserver.getRunningFormInfosByFilter(formInstanceFilter,(error: BusinessError, data: formInfo.RunningFormInfo[]) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfosByFilter, item count: ${data.length}`);
    }
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formInstanceFilter: formInfo.FormProviderFilter = {
  bundleName: "com.example.formprovide",
  abilityName: "EntryFormAbility",
  formName: "widget",
  moduleName: "entry"
}
try {
  formObserver.getRunningFormInfosByFilter(formInstanceFilter,
    (error: BusinessError | null, data: formInfo.RunningFormInfo[] | undefined) => {
      if (error) {
        console.error(`error, code: ${error.code}, message: ${error.message}`);
      } else {
        if (data != undefined) {
          for (let runningFormInfo of data) {
            console.info(`formObserver getRunningFormInfos, hostBundleName : ${runningFormInfo.hostBundleName}`);
          }
        }
      }
    });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## getRunningFormInfoById

getRunningFormInfoById(formId: string): Promise&lt;formInfo.RunningFormInfo&gt;

根据formId查询已添加的卡片信息。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填 | 说明                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formId     | string | 是   | 卡片标识。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | Promise对象。返回已添加的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000  | An internal functional error occurred. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId).then((data: formInfo.RunningFormInfo) => {
    console.info(`formObserver getRunningFormInfoById success, formId: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId).then((data: formInfo.RunningFormInfo) => {
    console.info(`formObserver getRunningFormInfoById success, formId: ${data.formId}`);
  }).catch((error) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## getRunningFormInfoById<sup>11+</sup>

getRunningFormInfoById(formId: string, isUnusedIncluded: boolean): Promise&lt;formInfo.RunningFormInfo&gt;

根据formId查询卡片已添加的卡片信息。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填 | 说明                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formId     | string | 是   | 卡片标识。 |
| isUnusedIncluded     | boolean | 是   | 表示是否包含未使用的卡片。<br>true: 表示包含未使用的卡片。<br>false: 表示不包含未使用的卡片。 |

**返回值：**

| 类型                | 说明                      |
| ------------------- | ------------------------- |
| Promise&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | Promise对象。返回已添加的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permissions denied.                             |
| 202      | The application is not a system application.                       |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000  | An internal functional error occurred. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId, true).then((data: formInfo.RunningFormInfo) => {
    console.info(`formObserver getRunningFormInfoById success, formId: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  formObserver.getRunningFormInfos(true).then((data: formInfo.RunningFormInfo[]) => {
    if (data !== undefined) {
      for (let runningFormInfo of data) {
        console.info(`formObserver getRunningFormInfos, hostBundleName : ${runningFormInfo.hostBundleName}`);
      }
    }
    if (data.length === 0) {
      console.error('testTag', 'formObserverStaticTest003 getRunningFormInfos no data');
    } else {
      try {
        formObserver.getRunningFormInfoById(data[0].formId, true).then((data) => {
          console.info('testTag', `formObserverStaticTest003 promise success`);
        }).catch((error: Error) => {
          let code = (error as BusinessError).code;
          let message = (error as BusinessError).message;
          hilog.error(DOMAIN, TAG, `formObserverStaticTest003 promise error, code: ${code} message: ${message}`);
        });
        console.info('testTag', 'formObserverStaticTest003 getRunningFormInfoById success');
      } catch (error: BusinessError) {
        hilog.error(DOMAIN, TAG,
          `formObserverStaticTest003 catch error, code: ${error.code} message: ${error.message}`);
      }
    }
  }).catch((error: Error) => {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`getRunningFormInfos error, code: ${code}, message: ${message}`);
  });
} catch (err: Error) {
  console.error('testTag', `getRunningFormInfos error，code: ${err?.code}, error message: ${err?.message}`);
}
```

## getRunningFormInfoById

getRunningFormInfoById(formId: string, callback: AsyncCallback&lt;formInfo.RunningFormInfo&gt;): void

根据提供方信息查询已添加的卡片信息。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填 | 说明                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formId     | string | 是   | 卡片标识。 |
| callback | AsyncCallback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是 | 回调函数。返回已添加的卡片信息。error为undefined，data为查询到的使用方列表信息；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000  | An internal functional error occurred. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId,(error: BusinessError, data: formInfo.RunningFormInfo) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfoById, formId: ${data.formId}`);
    }
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  formObserver.getRunningFormInfos().then((data: formInfo.RunningFormInfo[]) => {
    if (data !== undefined) {
      for (let runningFormInfo of data) {
        console.info(`formObserver getRunningFormInfos, hostBundleName : ${runningFormInfo.hostBundleName}`);
      }
    }
    if (data.length === 0) {
      console.error('testTag', 'formObserverStaticTest001 getRunningFormInfos no data');
    } else {
      try {
        formObserver.getRunningFormInfoById(data[0].formId, (error: BusinessError<void> | null,
          data: formInfo.RunningFormInfo | undefined) => {
          if (error?.code !== 0) {
            console.error('testTag',
              `formObserverStaticTest001 callback error, code:${error?.code} message:${error?.message}`);
          } else {
            console.info('testTag', `formObserverStaticTest001 callback success`);
          }
        });
      } catch (error: BusinessError) {
        hilog.error(DOMAIN, TAG,
          `formObserverStaticTest001 catch error, code:${error?.code} message:${error?.message}`);
      }
    }
  }).catch((error: Error) => {
    let code = (error as BusinessError).code;
    let message = (error as BusinessError).message;
    console.error(`getRunningFormInfos error, code: ${code}, message: ${message}`);
  });
} catch (err: Error) {
  console.error('testTag', `getRunningFormInfos error, code: ${err?.code}, error message: ${err?.message}`);
}
```

## getRunningFormInfoById<sup>11+</sup>

getRunningFormInfoById(formId: string, isUnusedIncluded: boolean, callback: AsyncCallback&lt;formInfo.RunningFormInfo&gt;): void

根据卡片标识formId，查询已添加的卡片信息。使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名      | 类型            | 必填 | 说明                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formId     | string | 是   | 卡片标识。 |
| isUnusedIncluded     | boolean | 是   | 表示是否包含未使用的卡片。<br>true: 表示包含未使用的卡片。<br>false: 表示不包含未使用的卡片。 |
| callback | AsyncCallback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是 | 回调函数。返回已添加的卡片信息。error为undefined，data为查询到的使用方列表信息；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[卡片错误码](errorcode-form.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201      | Permissions denied.                             |
| 202      | The application is not a system application.                       |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000  | An internal functional error occurred. |

**示例：**

ArkTS-Dyn示例：

```ts
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId, true, (error: BusinessError, data: formInfo.RunningFormInfo) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfoById, formId: ${data.formId}`);
    }
  });
} catch(error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  formObserver.getRunningFormInfos((error: BusinessError<void> | null,
    data: formInfo.RunningFormInfo[] | undefined) => {
    if (error?.code !== 0) {
      console.error('testTag',
        `formObserverStaticTest004 getRunningFormInfos callback error, code:${error?.code} message:${error?.message} `);
    } else {
      if (data !== undefined) {
        for (let runningFormInfo of data) {
          console.info(`formObserver getRunningFormInfos, hostBundleName : ${runningFormInfo.hostBundleName}`);
        }
      }
      if (data === undefined || data.length === 0) {
        console.error('testTag', 'formObserverStaticTest004 getRunningFormInfos callback no data');
      } else {
        try {
          formObserver.getRunningFormInfoById(data[0].formId, true,
            (error: BusinessError<void> | null, data: formInfo.RunningFormInfo | undefined) => {
              if (error?.code !== 0) {
                console.error('testTag',
                  `formObserverStaticTest004 getRunningFormInfoById callback error, code:${error?.code} message:${error?.message}`);
              } else {
                console.info('testTag', `formObserverStaticTest004 getRunningFormInfoById callback success`);
              }
            });
        } catch (error: BusinessError) {
          hilog.error(DOMAIN, TAG,
            `formObserverStaticTest004 getRunningFormInfoById catch error, code:${error?.code} message:${error?.message}`);
        }
      }
    }
  }, true);
} catch (err: BusinessError) {
  console.error('testTag', `getRunningFormInfos error code: ${err?.code}, error message: ${err?.message}`);
}
```

## on('router')<sup>11+</sup>

 on(type: 'router', observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                      |
| ---------------- | ---------------------------------------- | ---- | ----------------------------------------- |
| type             | string                                   | 是   | 填写'router'，表示订阅卡片的router事件。          |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发router事件的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Router event listening in registered form, formId: ${data.formId}`);
};
formObserver.on('router', callback);
```

## onRouter<sup>23+</sup>

onRouter(observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片router事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                     |
| ---------------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发router事件的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest015 observerCallback success`);
  };
  formObserver.onRouter(observerCallback);
  console.info('testTag', 'formObserverStaticTest015 formObserver on success');
  formObserver.offRouter(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest015 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest015 catch error, code: ${code}, message: ${message})`);
}
```

## on('router')<sup>11+</sup>

 on(type: 'router', hostBundleName: string, observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅指定卡片使用方的卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                                         |
| ---------------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | string                                   | 是   | 填写'router'，表示订阅卡片的router事件。                             |
| hostBundleName   | string                                   | 是   | 指定卡片使用方的bundleName。缺省则订阅所有卡片使用方的卡片的router事件。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发router事件的卡片信息。                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Router event listening in registered form, formId: ${data.formId}`);
};
formObserver.on('router', hostBundleName, callback);
```

## onRouter<sup>23+</sup>

onRouter(hostBundleName: string, observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅指定卡片使用方的卡片router事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定卡片使用方的bundleName。缺省则订阅所有卡片使用方的卡片的router事件。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发router事件的卡片信息。                     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest016 observerCallback success`);
  };
  formObserver.onRouter(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest016 formObserver on success');
  formObserver.offRouter(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest016 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest016 catch error, code: ${code}, message: ${message})`);
}
```

## off('router')<sup>11+</sup>

off(type: "router", hostBundleName?: string, observerCallback?: Callback&lt;formInfo.RunningFormInfo&gt;): void

取消订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                                         |
| ---------------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | string                                   | 是   | 填写'router'，表示取消订阅卡片的router事件。                             |
| hostBundleName   | string                                   | 否   | 指定订阅卡片使用方包的bundleName。<br>填写该参数时，与注册时填写bundleName的on接口对应。<br>缺省则订阅所有卡片使用方点击router类型卡片的事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回触发router事件的卡片信息。缺省时，表示注销对应bundleName下已注册事件回调。<br>需与对应on('router')的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Unregister form router event Listening, formId: ${data.formId}`);
};
formObserver.off('router', hostBundleName, callback);
```

> **说明：**
>
> - on('route', callback)与off('route', callback)相对应；
> - on('route', bundleName, callback)与off('route', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offRouter<sup>23+</sup>

offRouter(hostBundleName?: string, observerCallback?: Callback\<formInfo.RunningFormInfo\>): void

取消订阅卡片router事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定订阅卡片使用方包的bundleName。<br>填写该参数时，与注册时填写bundleName的on接口对应。<br>缺省则订阅所有卡片使用方点击router类型卡片的事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回触发router事件的卡片信息。缺省时，表示注销对应bundleName下已注册事件回调。<br>需与对应onRouter的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest015 observerCallback success`);
  };
  formObserver.onRouter(observerCallback);
  console.info('testTag', 'formObserverStaticTest015 formObserver on success');
  formObserver.offRouter(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest015 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest015 catch error, code: ${code}, message: ${message})`);
}
```

> **说明：**
>
> - onRouter(callback)与offRouter(callback)相对应；
> - onRouter(bundleName, callback)与offRouter( bundleName, callback)相对应；
> - 订阅（onRouter）只能由自己对应的取消订阅接口（offRouter）取消。

## on('message')<sup>11+</sup>

on(type: 'message', observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                      |
| ---------------- | ---------------------------------------- | ---- | ----------------------------------------- |
| type             | string                                   | 是   | 填写'message'，表示订阅卡片的message事件。         |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发message事件的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Message event listening in registered form, formId: ${data.formId}`);
};
formObserver.on('message', callback);
```

## onMessage<sup>23+</sup>

onMessage(observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片message事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                      |
| ---------------- | ------------------------------------------------------------ | ---- | ----------------------------------------- |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发message事件的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest013 observerCallback success`);
  };
  formObserver.onMessage(observerCallback);
  console.info('testTag', 'formObserverStaticTest013 formObserver on success');
  formObserver.offMessage(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest013 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest013 catch error, code: ${code}, message: ${message})`);
}
```

## on('message')<sup>11+</sup>

on(type: 'message', hostBundleName: string, observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅指定卡片使用方的卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                                         |
| ---------------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | string                                   | 是   | 填写'message'，表示订阅卡片的message事件。                            |
| hostBundleName   | string                                   | 是   | 指定卡片使用方的bundleName。缺省则订阅所有卡片使用方的卡片的message事件。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发message事件的卡片的信息。                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Message event listening in registered form, formId: ${data.formId}`);
};
formObserver.on('message', hostBundleName, callback);
```

## onMessage<sup>23+</sup>

onMessage(hostBundleName: string, observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅指定卡片使用方的卡片message事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定卡片使用方的bundleName。缺省则订阅所有卡片使用方的卡片的message事件。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发message事件的卡片的信息。                  |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest014 observerCallback success`);
  };
  formObserver.onMessage(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest014 formObserver on success');
  formObserver.offMessage(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest014 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest014 catch error, code: ${code}, message: ${message})`);
}
```

## off('message')<sup>11+</sup>

off(type: "message", hostBundleName?: string, observerCallback?: Callback&lt;formInfo.RunningFormInfo&gt;): void

取消订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片的信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                                         |
| ---------------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | string                                   | 是   | 填写'message'，表示取消订阅卡片的message事件。                         |
| hostBundleName   | string                                   | 否   | 指定订阅卡片使用方包的bundleName。<br>填写该参数时，与注册时填写bundleName的on接口对应。<br>缺省则取消订阅所有卡片使用方的点击事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回触发message事件的卡片的信息。缺省时，表示注销对应已注册事件回调。<br>需与对应on('message')的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Unregister form Message event Listening, formId: ${data.formId}`);
};
formObserver.off('message', hostBundleName, callback);
```

> **说明：**
>
> - on('message', callback)与off('message', callback)相对应；
> - on('message', bundleName, callback)与off('message', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offMessage<sup>23+</sup>

offMessage(hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void

取消订阅卡片message事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定订阅卡片使用方包的bundleName。<br>填写该参数时，与注册时填写bundleName的on接口对应。<br>缺省则取消订阅所有卡片使用方的点击事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回触发message事件的卡片的信息。缺省时，表示注销对应已注册事件回调。<br>需与对应onMessage的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest013 observerCallback success`);
  };
  formObserver.onMessage(observerCallback);
  console.info('testTag', 'formObserverStaticTest013 formObserver on success');
  formObserver.offMessage(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest013 formObserver off success');
} catch (error: BusinessError) {
  let code = (error as BusinessError).code;
  let message = (error as BusinessError).message;
  hilog.error(DOMAIN, TAG, `formObserverStaticTest013 catch error, code: ${code}, message: ${message})`);
}
```

> **说明：**
>
> - onMessage(callback)与offMessage(callback)相对应；
> - onMessage(bundleName, callback)与offMessage( bundleName, callback)相对应；
> - 订阅（onMessage）只能由自己对应的取消订阅接口（offMessage）取消。

## on('call')<sup>11+</sup>

on(type: 'call', observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                      |
| ---------------- | ---------------------------------------- | ---- | ----------------------------------------- |
| type             | string                                   | 是   | 填写'call'，表示订阅卡片的call事件。            |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发call事件的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Call event listening in registered form, formId: ${data.formId}`);
};
formObserver.on('call', callback);
```

## onCall<sup>23+</sup>

onCall(observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅卡片call事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                   |
| ---------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发call事件的卡片信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest011 observerCallback success`);
  };
  formObserver.onCall(observerCallback);
  console.info('testTag', 'formObserverStaticTest011 formObserver on success');
  formObserver.offCall(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest011 formObserver off success');
} catch (error: BusinessError) {
  hilog.error(DOMAIN, TAG, `formObserverStaticTest011 catch error, code: ${error.code} message: ${error.message}`);
}
```

## on('call')<sup>11+</sup>

on(type: 'call', hostBundleName: string, observerCallback: Callback&lt;formInfo.RunningFormInfo&gt;): void

订阅指定卡片使用方的卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                                         |
| ---------------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | string                                   | 是   | 填写'call'，表示订阅卡片的call事件。                               |
| hostBundleName   | string                                   | 是   | 指定卡片使用方的bundleName。缺省则订阅所有卡片使用方的卡片的call事件。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发call事件的卡片信息。                    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Call event listening in registered form, formId: ${data.formId}`);
};
formObserver.on('call', hostBundleName, callback);
```

## onCall<sup>23+</sup>

onCall(hostBundleName: string, observerCallback: Callback\<formInfo.RunningFormInfo\>): void

订阅指定卡片使用方的卡片call事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 是   | 指定卡片使用方的bundleName。缺省则订阅所有卡片使用方的卡片的call事件。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 是   | 回调函数。返回触发call事件的卡片信息。                       |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest012 observerCallback success`);
  };
  formObserver.onCall(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest012 formObserver on success');
  formObserver.offCall(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest012 formObserver off success');
} catch (error: BusinessError) {
  hilog.error(DOMAIN, TAG, `formObserverStaticTest012 catch error, code: ${error.code} message: ${error.message}`);
}
```

## off('call')<sup>11+</sup>

off(type: "call", hostBundleName?: string, observerCallback?: Callback&lt;formInfo.RunningFormInfo&gt;): void

取消订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Dyn。

**ArkTS-Dyn起始版本：** 11

**参数：**

| 参数名           | 类型                                     | 必填 | 说明                                                         |
| ---------------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| type             | string                                   | 是   | 填写'call'，表示取消订阅卡片的call事件。                           |
| hostBundleName   | string                                   | 否   | 指定订阅卡片使用方包的bundleName。<br>填写该参数时，与注册时填写bundleName的on接口对应。<br>缺省则取消订阅所有卡片使用方的点击事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回触发call事件的卡片信息。缺省时，表示注销对应已注册事件回调。<br>需与对应on('call')的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Unregister form Call event Listening, formId: ${data.formId}`);
};
formObserver.off('call', hostBundleName, callback);
```

> **说明：**
>
> - on('call', callback)与off('call', callback)相对应；
> - on('call', bundleName, callback)与off('call', bundleName, callback)相对应；
> - 订阅（on）只能由自己对应的取消订阅接口（off）取消。

## offCall<sup>23+</sup>

offCall(hostBundleName?: string, observerCallback?: Callback\<formInfo.RunningFormInfo\>): void

取消订阅卡片call事件。使用callback异步回调。

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名           | 类型                                                         | 必填 | 说明                                                         |
| ---------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| hostBundleName   | string                                                       | 否   | 指定订阅卡片使用方包的bundleName。<br>填写该参数时，与注册时填写bundleName的on接口对应。<br>缺省则取消订阅所有卡片使用方的点击事件，与注册时未填写bundleName的on接口相对应。 |
| observerCallback | Callback&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo-sys.md#runningforminfo10)&gt; | 否   | 回调函数。返回触发call事件的卡片信息。缺省时，表示注销对应已注册事件回调。<br>需与对应onCall的callback一致。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例：**

```ts
'use static'

import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN: int = 0x0000;
const TAG: string = 'testTag formAgentTest';

try {
  let hostBundleName: string = 'com.example.demoForm';
  let observerCallback = (data: formInfo.RunningFormInfo | undefined) => {
    console.info('testTag', `formObserverStaticTest011 observerCallback success`);
  };
  formObserver.onCall(observerCallback);
  console.info('testTag', 'formObserverStaticTest011 formObserver on success');
  formObserver.offCall(hostBundleName, observerCallback);
  console.info('testTag', 'formObserverStaticTest011 formObserver off success');
} catch (error: BusinessError) {
  hilog.error(DOMAIN, TAG, `formObserverStaticTest011 catch error, code: ${error.code} message: ${error.message}`);
}
```

> **说明：**
>
> - onCall(callback)与offCall(callback)相对应；
> - onCall(bundleName, callback)与offCall( bundleName, callback)相对应；
> - 订阅（onCall）只能由自己对应的取消订阅接口（offCall）取消。
