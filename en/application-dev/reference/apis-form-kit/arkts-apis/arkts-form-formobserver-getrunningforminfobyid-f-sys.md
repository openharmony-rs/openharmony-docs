# getRunningFormInfoById (System API)

## Modules to Import

```TypeScript
import { formObserver } from '@kit.FormKit';
```

<a id="getrunningforminfobyid1"></a>

## getRunningFormInfoById

```TypeScript
function getRunningFormInfoById(formId: string): Promise<formInfo.RunningFormInfo>
```

Obtains the RunningFormInfo object by formId.

**Since:** 10

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

**Model restriction:** This API can be used only in the stage model.

<!--Device-formObserver-function getRunningFormInfoById(formId: string): Promise<formInfo.RunningFormInfo>--><!--Device-formObserver-function getRunningFormInfoById(formId: string): Promise<formInfo.RunningFormInfo>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the form provider formId. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId).then((data: formInfo.RunningFormInfo) => {
    console.info(`formObserver getRunningFormInfoById success, formId: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->


<a id="getrunningforminfobyid2"></a>

## getRunningFormInfoById

```TypeScript
function getRunningFormInfoById(formId: string, isUnusedIncluded: boolean): Promise<formInfo.RunningFormInfo>
```

Obtains the RunningFormInfo object by formId.

**Since:** 11

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

**Model restriction:** This API can be used only in the stage model.

<!--Device-formObserver-function getRunningFormInfoById(formId: string, isUnusedIncluded: boolean): Promise<formInfo.RunningFormInfo>--><!--Device-formObserver-function getRunningFormInfoById(formId: string, isUnusedIncluded: boolean): Promise<formInfo.RunningFormInfo>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the form provider formId. |
| isUnusedIncluded | boolean | Yes | Indicates whether to include unused form. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId, true).then((data: formInfo.RunningFormInfo) => {
    console.info(`formObserver getRunningFormInfoById success, formId: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->


<a id="getrunningforminfobyid3"></a>

## getRunningFormInfoById

```TypeScript
function getRunningFormInfoById(formId: string, callback: AsyncCallback<formInfo.RunningFormInfo>): void
```

Obtains the RunningFormInfo object by formId.

**Since:** 10

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

**Model restriction:** This API can be used only in the stage model.

<!--Device-formObserver-function getRunningFormInfoById(formId: string, callback: AsyncCallback<formInfo.RunningFormInfo>): void--><!--Device-formObserver-function getRunningFormInfoById(formId: string, callback: AsyncCallback<formInfo.RunningFormInfo>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the form provider formId. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | Yes | The callback of getFormInstancesById. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |

<!--Del-->
**Examples**

```TypeScript
import { formInfo, formObserver } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formObserver.getRunningFormInfoById(formId, (error: BusinessError, data: formInfo.RunningFormInfo) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formObserver getRunningFormInfoById, formId: ${data.formId}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->


<a id="getrunningforminfobyid4"></a>

## getRunningFormInfoById

```TypeScript
function getRunningFormInfoById(
    formId: string,
    isUnusedIncluded: boolean,
    callback: AsyncCallback<formInfo.RunningFormInfo>
  ): void
```

Obtains the RunningFormInfo object by formId.

**Since:** 11

**Required permissions:** ohos.permission.OBSERVE_FORM_RUNNING

**Model restriction:** This API can be used only in the stage model.

<!--Device-formObserver-function getRunningFormInfoById(    formId: string,    isUnusedIncluded: boolean,    callback: AsyncCallback<formInfo.RunningFormInfo>  ): void--><!--Device-formObserver-function getRunningFormInfoById(    formId: string,    isUnusedIncluded: boolean,    callback: AsyncCallback<formInfo.RunningFormInfo>  ): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formId | string | Yes | Indicates the form provider formId. |
| isUnusedIncluded | boolean | Yes | Indicates whether to include unused form. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[formInfo.RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md)&gt; | Yes | The callback of getFormInstancesById. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500100](../errorcode-form.md#16500100-failed-to-obtain-widget-configuration-information) | Failed to obtain the configuration information. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |

<!--Del-->
**Examples**

```TypeScript
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
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

<!--DelEnd-->
