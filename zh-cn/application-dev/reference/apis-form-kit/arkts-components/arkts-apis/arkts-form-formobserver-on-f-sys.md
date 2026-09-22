# on（系统接口）

## 导入模块

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## on('formAdd')

```TypeScript
function on(type: 'formAdd', observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片新增事件。使用callback异步回调，返回当前新增卡片的信息。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formAdd' | 是 | 填写'formAdd'，表示卡片新增事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回当前新增卡片的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.on('formAdd', callback);
```


## on('formAdd')

```TypeScript
function on(type: 'formAdd', hostBundleName: string, observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片新增事件。使用callback异步回调，返回指定卡片使用方应用新增卡片的信息。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formAdd' | 是 | 填写'formAdd'，表示卡片新增事件。 |
| hostBundleName | string | 是 | 指定订阅卡片使用方包的bundleName。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回指定卡片使用方应用新增卡片的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.on('formAdd', bundleName, callback);
```


## on('formRemove')

```TypeScript
function on(type: 'formRemove', observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片删除事件。使用callback异步回调，返回当前删除卡片的信息。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formRemove' | 是 | 填写'formRemove'，表示卡片删除事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回当前删除卡片的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`form deleted, formId: ${data.formId}`);
}

formObserver.on('formRemove', callback);
```


## on('formRemove')

```TypeScript
function on(type: 'formRemove', hostBundleName: string, observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片删除事件。使用callback异步回调，返回指定卡片使用方应用被删除卡片的信息。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'formRemove' | 是 | 填写'formRemove'，表示卡片删除事件。 |
| hostBundleName | string | 是 | 指定订阅卡片使用方包的bundleName。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回指定卡片使用方应用被删除卡片的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`form deleted, formId: ${data.formId}`);
}

formObserver.on('formRemove', bundleName, callback);
```


## on('notifyVisible')

```TypeScript
function on(type: 'notifyVisible', observerCallback: Callback<Array<formInfo.RunningFormInfo>>): void
```

订阅通知卡片可见的事件。使用callback异步回调。

​触发通知卡片可见场景为：调用[notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)接口通知对应卡片可见性变更为可见状态。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'notifyVisible' | 是 | 仅允许填写'notifyVisible'，表示订阅通知卡片可见的事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt;&gt; | 是 | 回调函数。返回订阅该事件的卡片信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo[]) => {
  data.forEach(item => {
    console.info(`form change visibility, formId: ${item.formId}`);
  });
}

formObserver.on('notifyVisible', callback);
```


## on('notifyVisible')

```TypeScript
function on(
    type: 'notifyVisible',
    hostBundleName: string,
    observerCallback: Callback<Array<formInfo.RunningFormInfo>>
  ): void
```

订阅通知卡片可见的事件。使用callback异步回调。

​触发通知卡片可见场景为：调用[notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md)接口通知对应卡片可见性变更为可见状态。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'notifyVisible' | 是 | 仅允许填写'notifyVisible'，表示订阅通知卡片可见的事件。 |
| hostBundleName | string | 是 | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt;&gt; | 是 | 回调函数。返回订阅该事件的卡片信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  data.forEach(item => {
    console.info(`form change visibility, formId: ${item.formId}`);
  });
}

formObserver.on('notifyVisible', bundleName, callback);
```


## on('notifyInvisible')

```TypeScript
function on(type: 'notifyInvisible', observerCallback: Callback<Array<formInfo.RunningFormInfo>>): void
```

订阅通知卡片不可见的事件。使用callback异步回调。

​触发通知卡片不可见场景为：调用[notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md)接口通知对应卡片可见性变更为不可见状态。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'notifyInvisible' | 是 | 仅允许填写'notifyInvisible'，表示订阅卡片不可见的事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt;&gt; | 是 | 回调函数。返回订阅通知卡片不可见的卡片信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo[]) => {
  data.forEach(item => {
    console.info(`form change invisibility, formId: ${item.formId}`);
  });
}

formObserver.on('notifyInvisible', callback);
```


## on('notifyInvisible')

```TypeScript
function on(
    type: 'notifyInvisible',
    hostBundleName: string,
    observerCallback: Callback<Array<formInfo.RunningFormInfo>>,
  ): void
```

订阅通知卡片不可见的事件。使用callback异步回调。

​触发通知卡片不可见场景为：调用[notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md)接口通知对应卡片可见性变更为不可见状态。

**起始版本：** 10

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'notifyInvisible' | 是 | 仅允许填写'notifyInvisible'，表示订阅卡片不可见的事件。 |
| hostBundleName | string | 是 | 指定卡片使用方的bundleName，用于订阅卡片在该使用方的可见状态变更事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt;&gt; | 是 | 回调函数。返回订阅通知卡片不可见的卡片信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |


## on('router')

```TypeScript
function on(type: 'router', observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'router' | 是 | 填写'router'，表示订阅卡片的router事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回触发router事件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Router event listening in registered form. ID: ${data.formId}`);
};
formObserver.on('router', callback);
```


## on('router')

```TypeScript
function on(type: 'router', hostBundleName: string, observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅指定卡片使用方的卡片router事件。使用callback异步回调，返回触发router事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'router' | 是 | 填写'router'，表示订阅卡片的router事件。 |
| hostBundleName | string | 是 | 指定卡片使用方的bundleName。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回触发router事件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Router event listening in registered form. ID: ${data.formId}`);
};
formObserver.on('router', hostBundleName, callback);
```


## on('message')

```TypeScript
function on(type: 'message', observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 填写'message'，表示订阅卡片的message事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回触发message事件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Message event listening in registered form. ID: ${data.formId}`);
};
formObserver.on('message', callback);
```


## on('message')

```TypeScript
function on(type: 'message', hostBundleName: string, observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅指定卡片使用方的卡片message事件。使用callback异步回调，返回触发message事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'message' | 是 | 填写'message'，表示订阅卡片的message事件。 |
| hostBundleName | string | 是 | 指定卡片使用方的bundleName。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回触发message事件的卡片的信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Message event listening in registered form. ID: ${data.formId}`);
};
formObserver.on('message', hostBundleName, callback);
```


## on('call')

```TypeScript
function on(type: 'call', observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'call' | 是 | 填写'call'，表示订阅卡片的call事件。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回触发call事件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Call event listening in registered form. ID: ${data.formId}`);
};
formObserver.on('call', callback);
```


## on('call')

```TypeScript
function on(type: 'call', hostBundleName: string, observerCallback: Callback<formInfo.RunningFormInfo>): void
```

订阅指定卡片使用方的卡片call事件。使用callback异步回调，返回触发call事件的卡片信息。

**起始版本：** 11

**需要权限：** ohos.permission.OBSERVE_FORM_RUNNING

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'call' | 是 | 填写'call'，表示订阅卡片的call事件。 |
| hostBundleName | string | 是 | 指定卡片使用方的bundleName。 |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | 是 | 回调函数。返回触发call事件的卡片信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**示例**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Call event listening in registered form. ID: ${data.formId}`);
};
formObserver.on('call', hostBundleName, callback);
```
