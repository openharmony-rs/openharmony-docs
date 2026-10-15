# off (System API)

## Modules to Import

```TypeScript
import { formObserver } from '@kit.FormKit';
```

## off('formAdd')

```TypeScript
function off(type: 'formAdd', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

Cancels listening to the event of add form. <p>You can use this method to cancel listening to the event of add form.</p>

**Since:** 10

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(type: 'formAdd', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void--><!--Device-formObserver-function off(type: 'formAdd', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'formAdd' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.off('formAdd', bundleName, callback);
```

<!--DelEnd-->


## off('formRemove')

```TypeScript
function off(type: 'formRemove', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

Cancels listening to the event of remove form. <p>You can use this method to cancel listening to the event of remove form.</p>

**Since:** 10

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(type: 'formRemove', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void--><!--Device-formObserver-function off(type: 'formRemove', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'formRemove' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`a new form added, formId: ${data.formId}`);
}

formObserver.off('formRemove', bundleName, callback);
```

<!--DelEnd-->


## off('notifyVisible')

```TypeScript
function off(
    type: 'notifyVisible',
    hostBundleName?: string,
    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>
  ): void
```

Cancels listening to the event of notifyVisible type change. <p>You can use this method to cancel listening to the event of notifyVisible type change.</p>

**Since:** 10

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(    type: 'notifyVisible',    hostBundleName?: string,    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>  ): void--><!--Device-formObserver-function off(    type: 'notifyVisible',    hostBundleName?: string,    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>  ): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'notifyVisible' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt;&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  data.forEach(data => {
    console.info(`form change visibility, formId: ${data.formId}`);
  });
}

formObserver.off('notifyVisible', bundleName, callback);
```

<!--DelEnd-->


## off('notifyInvisible')

```TypeScript
function off(
    type: 'notifyInvisible',
    hostBundleName?: string,
    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>
  ): void
```

Cancels listening to the event of notifyInvisible type change. <p>You can use this method to cancel listening to the event of notifyInvisible type change.</p>

**Since:** 10

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(    type: 'notifyInvisible',    hostBundleName?: string,    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>  ): void--><!--Device-formObserver-function off(    type: 'notifyInvisible',    hostBundleName?: string,    observerCallback?: Callback<Array<formInfo.RunningFormInfo>>  ): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'notifyInvisible' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt;&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let bundleName: string = 'ohos.samples.FormApplication';

let callback = (data: formInfo.RunningFormInfo[]) => {
  data.forEach(data => {
    console.info(`form change invisibility, formId: ${data.formId}`);
  });
}

formObserver.off('notifyInvisible', bundleName, callback);
```

<!--DelEnd-->


## off('router')

```TypeScript
function off(type: 'router', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

Unregister form router event Listening.

**Since:** 11

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(type: 'router', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void--><!--Device-formObserver-function off(type: 'router', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'router' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Unregister form router event Listening. ID: ${data.formId}`);
};
formObserver.off('router', hostBundleName, callback);
```

<!--DelEnd-->


## off('message')

```TypeScript
function off(type: 'message', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

Unregister form message event Listening.

**Since:** 11

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(type: 'message', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void--><!--Device-formObserver-function off(type: 'message', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'message' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Unregister from Message event Listening. ID: ${data.formId}`);
};
formObserver.off('message', hostBundleName, callback);
```

<!--DelEnd-->


## off('call')

```TypeScript
function off(type: 'call', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void
```

Unregister form call event Listening.

**Since:** 11

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

<!--Device-formObserver-function off(type: 'call', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void--><!--Device-formObserver-function off(type: 'call', hostBundleName?: string, observerCallback?: Callback<formInfo.RunningFormInfo>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'call' | Yes | Indicates event type. |
| hostBundleName | string | No | Indicates the bundle name of the form host application. |
| observerCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | No | The callback is used to return the running form info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';

let hostBundleName: string = 'ohos.samples.FormApplication';
let callback = (data: formInfo.RunningFormInfo) => {
  console.info(`Unregister form Call event Listening. ID: ${data.formId}`);
};
formObserver.off('call', hostBundleName, callback);
```

<!--DelEnd-->
