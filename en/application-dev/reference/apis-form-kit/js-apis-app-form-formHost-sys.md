# @ohos.app.form.formHost (formHost) (System API)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=ecaccbf249e6a7771624e675ca80e1f5142e1256 translatedAt=2026-11-03T06:53:19.542Z pushedAt=2026-11-04T03:11:19.935Z nl=1 -->

The formHost module provides the capabilities of form host related APIs, including deleting, releasing, requesting updates, obtaining card information, and querying status of forms installed under the same user of the form host.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are all system APIs.

## Modules to Import

```ts
import { formHost } from '@kit.FormKit';
```

## formHost.deleteForm

deleteForm(formId: string, callback: AsyncCallback&lt;void&gt;): void

Deletes a specified form. After this method is called, the application will be unable to use the form, and the form management service will no longer retain information about the form. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the specified form is deleted successfully, **error** is **undefined**; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.deleteForm(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('formHost deleteForm success');
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.deleteForm

deleteForm(formId: string): Promise&lt;void&gt;

Deletes a specified form. After this method is called, the application will be unable to use the form, and the form management service will no longer retain information about the form. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------- |
| formId | string | Yes | Card ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';

try {
  let formId: string = '12400633174999288';
  formHost.deleteForm(formId).then(() => {
    console.info('formHost deleteForm success');
  }).catch((error: BusinessError) => {
    console.error(`formHost deleteForm, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.releaseForm

releaseForm(formId: string, callback: AsyncCallback&lt;void&gt;): void

Releases the specified card. After this method is called, the application will be unable to use the card, but the card management service still retains the cached information and stored information about the card. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the specified card is released successfully, **error** is **undefined**; otherwise, **error** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.releaseForm(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.releaseForm

releaseForm(formId: string, isReleaseCache: boolean, callback: AsyncCallback&lt;void&gt;): void

Releases the specified form. After this method is called, the application will be unable to use the form, and the card management service retains the storage information about the form. You can choose whether to retain the cache information. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| -------------- | ------  | ---- | ----------- |
| formId         | string  | Yes   | Card ID.     |
| isReleaseCache | boolean | Yes   | Whether to release the cache.<br>true: release the cache.<br>false: do not release the cache. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the specified form is released successfully, **error** is **undefined**; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.releaseForm(formId, true, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.releaseForm

releaseForm(formId: string, isReleaseCache?: boolean): Promise&lt;void&gt;

Releases the specified form. After this method is called, the application will be unable to use the form, and the card management service retains the storage information about the form. You can choose whether to retain the cache information. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| -------------- | ------  | ---- | ----------- |
| formId         | string  | Yes  | Card ID.     |
| isReleaseCache | boolean | No  | Whether to release the cache. The default value is **false**.<br>**true**: release the cache.<br>**false**: do not release the cache.  |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.releaseForm(formId, true).then(() => {
    console.info('formHost releaseForm success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.requestForm

requestForm(formId: string, callback: AsyncCallback&lt;void&gt;): void

Requests a card update. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result. If the card update request is successful, **error** is **undefined**. Otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.requestForm(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.requestForm

requestForm(formId: string): Promise&lt;void&gt;

Requests a card update. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.requestForm(formId).then(() => {
    console.info('formHost requestForm success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.requestFormWithParams<sup>12+</sup>

requestFormWithParams(formId: string, wantParams?: Record<string, Object>): Promise&lt;void&gt;

Requests a form update with parameters. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| wantParams | Record<string, Object> | No   | Update parameters. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  let params: Record<string, Object> = {
    'ohos.extra.param.key.host_bg_inverse_color': '#ff000000' as Object
  };
  formHost.requestFormWithParams(formId, params).then(() => {
    console.info('formHost requestFormWithParams success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.castToNormalForm

castToNormalForm(formId: string, callback: AsyncCallback&lt;void&gt;): void

Converts a specified temporary form into a normal form. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the specified temporary form is converted into a normal form successfully, **error** is **undefined**; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501002 | The number of forms exceeds the maximum allowed. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.castToNormalForm(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.castToNormalForm

castToNormalForm(formId: string): Promise&lt;void&gt;

Converts the specified temporary form into a normal form. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------- |
| formId | string | Yes | Card ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501002 | The number of forms exceeds the maximum allowed. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.castToNormalForm(formId).then(() => {
    console.info('formHost castToNormalForm success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyVisibleForms

notifyVisibleForms(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sends a notification to the card framework to make the specified cards visible. After this method is called successfully, onVisibilityChange is invoked to notify the card provider. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds  | Array&lt;string&gt;       | Yes   | List of card IDs.         |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the notification is sent to the card framework to make the specified cards visible successfully, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.notifyVisibleForms(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyVisibleForms

notifyVisibleForms(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Sends a notification to the card framework to make the specified cards visible. After this method is called successfully, onVisibilityChange is invoked to notify the form provider. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.notifyVisibleForms(formId).then(() => {
    console.info('formHost notifyVisibleForms success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyInvisibleForms

notifyInvisibleForms(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sends a notification to the card framework to make the specified cards invisible. After this method is called successfully, onVisibilityChange is invoked to notify the form provider. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds  | Array&lt;string&gt;       | Yes   | List of card IDs.|
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the notification is sent to the card framework to make the specified cards invisible successfully, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Errors](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.notifyInvisibleForms(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyInvisibleForms

notifyInvisibleForms(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Sends a notification to the card framework to make the specified cards invisible. After this method is called successfully, onVisibilityChange is invoked to notify the card provider. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.notifyInvisibleForms(formId).then(() => {
    console.info('formHost notifyInvisibleForms success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.enableFormsUpdate

enableFormsUpdate(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sends a notification to the card framework to make the specified cards updatable. After this method is called successfully, the card refresh status is set to enabled, and the cards can receive updates from the card provider. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------- |
| formIds  | Array&lt;string&gt;       | Yes   | List of card IDs.         |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the notification is sent to the card framework to make the specified cards updatable successfully, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.enableFormsUpdate(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.enableFormsUpdate

enableFormsUpdate(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Sends a notification to the card framework to enable the specified cards to be updated. After this API is called successfully, the card refresh status is set to enabled, and the cards can receive updates from the card provider. This API uses a promise to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Errors](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.enableFormsUpdate(formId).then(() => {
    console.info('formHost enableFormsUpdate success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.disableFormsUpdate

disableFormsUpdate(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sends a notification to the card framework to make the specified cards unable to be updated. After this method is called successfully, the card refresh status is set to disabled, and the cards cannot receive updates from the form provider. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds  | Array&lt;string&gt;       | Yes   | List of card IDs.         |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. If the notification is sent to the card framework to make the specified cards unable to be updated successfully, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.disableFormsUpdate(formId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.disableFormsUpdate

disableFormsUpdate(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Sends a notification to the card framework to make the specified cards unable to be updated. After this method is called successfully, the card refresh status is set to disabled, and the cards cannot receive updates from the form provider. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string[] = ['12400633174999288'];
  formHost.disableFormsUpdate(formId).then(() => {
    console.info('formHost disableFormsUpdate success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.isSystemReady

isSystemReady(callback: AsyncCallback&lt;void&gt;): void

Checks whether the system is ready. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the system is ready, **error** is **undefined**; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application.   |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.isSystemReady((error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.isSystemReady

isSystemReady(): Promise&lt;void&gt;

Checks whether the system is ready. This API uses a promise to return the result.

**System capability:** SystemCapability.Ability.Form

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application.   |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.isSystemReady().then(() => {
    console.info('formHost isSystemReady success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.getAllFormsInfo

getAllFormsInfo(callback: AsyncCallback&lt;Array&lt;formInfo.FormInfo&gt;&gt;): void

Obtains the card information provided by all applications on the device (excluding template cards). This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type                                                                                           | Mandatory | Description    |
| ------ |----------------------------------------------------------------------------------------------| ---- | ------- |
| callback | AsyncCallback&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Yes | Callback used to return the result. If the card information provided by all applications on the device is obtained successfully, **error** is **undefined** and **data** is the retrieved card information; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';

try {
  formHost.getAllFormsInfo((error: BusinessError, data: formInfo.FormInfo[]) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('formHost getAllFormsInfo success.');
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.getAllFormsInfo

getAllFormsInfo(): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains the card information provided by all applications on the device (excluding template forms). This API uses a promise to return the result.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Return value**

| Type                                                                                     | Description                    |
|:---------------------------------------------------------------------------------------|:----------------------|
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Promise used to return the card information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';

try {
  formHost.getAllFormsInfo().then((data: formInfo.FormInfo[]) => {
    console.info('formHost getAllFormsInfo success.');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.getFormsInfo

getFormsInfo(bundleName: string, callback: AsyncCallback&lt;Array&lt;formInfo.FormInfo&gt;&gt;): void

Obtains the card information provided by a specified application on the device (excluding template forms). This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type                                                                                           | Mandatory | Description    |
| ------ |----------------------------------------------------------------------------------------------| ---- | ------- |
| bundleName | string                                                                                       | Yes | Bundle name of the application to query. |
| callback | AsyncCallback&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Yes | Callback invoked to return the result. If the card information of the specified application on the device is obtained successfully, error is undefined and data is the retrieved card information; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';

try {
  formHost.getFormsInfo('com.example.ohos.formjsdemo', (error: BusinessError, data: formInfo.FormInfo[]) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('formHost getFormsInfo success.');
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.getFormsInfo

getFormsInfo(bundleName: string, moduleName: string, callback: AsyncCallback&lt;Array&lt;formInfo.FormInfo&gt;&gt;): void

Obtains the card information provided by a specified application on the device (excluding template forms). This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type                                                                                           | Mandatory | Description    |
| ------ |----------------------------------------------------------------------------------------------| ---- | ------- |
| bundleName | string                                                                                       | Yes | Bundle name of the application to query. |
| moduleName | string                                                                                       | Yes |  Name of the module to query. |
| callback | AsyncCallback&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Yes | Callback used to return the result. If the card information provided by the specified application on the device is obtained successfully, **error** is **undefined** and **data** is the retrieved card information; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';

try {
  formHost.getFormsInfo('com.example.ohos.formjsdemo', 'entry', (error: BusinessError, data: formInfo.FormInfo[]) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('formHost getFormsInfo success.');
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.getFormsInfo

getFormsInfo(bundleName: string, moduleName?: string): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains the card information provided by a specified application on the device (excluding template forms). This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| bundleName | string | Yes | Bundle name of the application to query. |
| moduleName | string | No |  Name of the module to query. The default value is an empty string. |

**Return value**

| Type                                                                                     | Description                                |
|:---------------------------------------------------------------------------------------| :---------------------------------- |
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Promise used to return the card information obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';

try {
  formHost.getFormsInfo('com.example.ohos.formjsdemo', 'entry').then((data: formInfo.FormInfo[]) => {
    console.info('formHost getFormsInfo success.');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.getFormsInfo<sup>12+</sup>

getFormsInfo(filter: formInfo.FormInfoFilter): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains the card information provided by a specified application on the device (excluding template forms). This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| filter | [formInfo.FormInfoFilter](js-apis-app-form-formInfo.md#forminfofilter) | Yes | Card information filter. |

**Return value**

| Type          | Description                                |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md)&gt;&gt; | Promise object. Returns the card information that matches the filter. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application.  |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.  |
| 16500060 | Service connection error.  |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';

const filter: formInfo.FormInfoFilter = {
  bundleName: 'ohos.samples.FormApplication',
  moduleName: 'entry',
  supportedDimensions: [FormDimension.Dimension_1_2, FormDimension.Dimension_2_2, FormDimension.Dimension_2_4]
};
try {
  formHost.getFormsInfo(filter).then((data: formInfo.FormInfo[]) => {
    console.info('formHost getFormsInfo success.');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.deleteInvalidForms

deleteInvalidForms(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;number&gt;): void

Deletes the forms of the application that are not in the valid list based on the valid form list. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of valid card IDs. |
| callback | AsyncCallback&lt;number&gt; | Yes | Callback invoked to return the result. If the invalid forms of the application are deleted based on the list, **error** is **undefined** and **data** is the number of deleted forms; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';

try {
  let formIds: string[] = new Array('12400633174999288', '12400633174999289');
  formHost.deleteInvalidForms(formIds, (error: BusinessError, data: number) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formHost deleteInvalidForms, data: ${data}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.deleteInvalidForms

deleteInvalidForms(formIds: Array&lt;string&gt;): Promise&lt;number&gt;

Deletes the invalid forms of an application based on the list. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of valid card IDs. |

**Return value**

| Type          | Description                                |
| :------------ | :---------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of deleted forms. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';

try {
  let formIds: string[] = new Array('12400633174999288', '12400633174999289');
  formHost.deleteInvalidForms(formIds).then((data: number) => {
    console.info(`formHost deleteInvalidForms, data: ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.acquireFormState

acquireFormState(want: Want, callback: AsyncCallback&lt;formInfo.FormStateInfo&gt;): void

Obtains the form state. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Want information carried when querying the form state. It must contain the bundle name, ability name, module name, form name, form dimension, and so on. |
| callback | AsyncCallback&lt;[formInfo.FormStateInfo](js-apis-app-form-formInfo.md#formstateinfo)&gt; | Yes | Callback invoked to return the result. If the form state is obtained successfully, **error** is **undefined** and **data** is the form state obtained; otherwise, **error** is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  'deviceId': '',
  'bundleName': 'ohos.samples.FormApplication',
  'abilityName': 'FormAbility',
  'parameters': {
    'ohos.extra.param.key.module_name': 'entry',
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.form_dimension': 2
  }
};
try {
  formHost.acquireFormState(want, (error: BusinessError, data: formInfo.FormStateInfo) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info(`formHost acquireFormState, data: ${data.formState}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.acquireFormState

acquireFormState(want: Want): Promise&lt;formInfo.FormStateInfo&gt;

Obtains the form state. This API uses a promise to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| want   | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Want information carried when querying the form state. It must contain the bundle name, ability name, module name, form name, and form dimension. |

**Return value**

| Type          | Description                                |
| :------------ | :---------------------------------- |
| Promise&lt;[formInfo.FormStateInfo](js-apis-app-form-formInfo.md#formstateinfo)&gt; | Promise used to return the form state. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let want: Want = {
  'deviceId': '',
  'bundleName': 'ohos.samples.FormApplication',
  'abilityName': 'FormAbility',
  'parameters': {
    'ohos.extra.param.key.module_name': 'entry',
    'ohos.extra.param.key.form_name': 'widget',
    'ohos.extra.param.key.form_dimension': 2
  }
};
try {
  formHost.acquireFormState(want).then((data: formInfo.FormStateInfo) => {
    console.info(`formHost acquireFormState, data: ${data.formState}`);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.on('formUninstall')

on(type: 'formUninstall', callback: Callback&lt;string&gt;): void

Subscribes to the form uninstall event. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> Form uninstall is different from form removal. When an application is uninstalled, the corresponding forms are uninstalled automatically.

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| type | string | Yes   | Set this parameter to 'formUninstall', which indicates the form uninstall event. |
| callback | Callback&lt;string&gt; | Yes | Callback invoked to return the card ID. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

```ts
import { formHost } from '@kit.FormKit';

formHost.on('formUninstall', (formId: string) => {
  console.info(`formHost on formUninstall, formId: ${formId}`);
});
```

## formHost.off('formUninstall')

off(type: 'formUninstall', callback?: Callback&lt;string&gt;): void

Unsubscribes from the form uninstall event. This API uses an asynchronous callback to return the result.

> **NOTE**
> 
> Form uninstall is different from form removal. When an application is uninstalled, the corresponding forms are automatically uninstalled.

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| type | string | Yes   | Set this parameter to 'formUninstall', which indicates the form uninstall event. |
| callback | Callback&lt;string&gt; | No | Callback for the form uninstall event, which returns the card ID. If this parameter is left unspecified, all registered event callbacks are unregistered.<br> This callback must be the same as the callback in the corresponding on('formUninstall'). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |

**Example**

```ts
import { formHost } from '@kit.FormKit';

formHost.off('formUninstall', (formId: string) => {
  console.info(`formHost on formUninstall, formId: ${formId}`);
});
```

## formHost.notifyFormsVisible

notifyFormsVisible(formIds: Array&lt;string&gt;, isVisible: boolean, callback: AsyncCallback&lt;void&gt;): void

Notifies whether a form is visible. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |
| isVisible | boolean | Yes   | Whether the form is visible.<br>true: The form is visible.<br>false: The form is invisible. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the notification of form visibility succeeds, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsVisible(formIds, true, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyFormsVisible

notifyFormsVisible(formIds: Array&lt;string&gt;, isVisible: boolean): Promise&lt;void&gt;

Notifies whether a form is visible. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |
| isVisible | boolean | Yes   | Whether the form is visible.<br>true: The form is visible.<br>false: The form is invisible. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsVisible(formIds, true).then(() => {
    console.info('formHost notifyFormsVisible success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyFormsEnableUpdate

notifyFormsEnableUpdate(formIds: Array&lt;string&gt;, isEnableUpdate: boolean, callback: AsyncCallback&lt;void&gt;): void

Notifies whether to enable the update status of a form. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |
| isEnableUpdate | boolean | Yes   | Whether to enable the update status of the form.<br>true: The update status of the form is enabled. false: The update status of the form is not enabled.|
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the notification of whether to enable the update status of the form is successful, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsEnableUpdate(formIds, true, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyFormsEnableUpdate

notifyFormsEnableUpdate(formIds: Array&lt;string&gt;, isEnableUpdate: boolean): Promise&lt;void&gt;

Notifies whether to enable the update status of a form. This API uses a promise to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array&lt;string&gt; | Yes   | List of card IDs. |
| isEnableUpdate | boolean | Yes   | Whether to enable the update status of the form.<br>true: The update status of the form is enabled.<br>false: The update status of the form is not enabled. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsEnableUpdate(formIds, true).then(() => {
    console.info('formHost notifyFormsEnableUpdate success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
## formHost.shareForm

shareForm(formId: string, deviceId: string, callback: AsyncCallback&lt;void&gt;): void

Shares a form with the specified form ID and remote device ID. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| deviceId | string | Yes   | Remote device ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked to return the result. If the form is shared successfully with the specified form ID and remote device ID, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
let deviceId: string = 'EFC11C0C53628D8CC2F8CB5052477E130D075917034613B9884C55CD22B3DEF2';
try {
  formHost.shareForm(formId, deviceId, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.shareForm

shareForm(formId: string, deviceId: string): Promise&lt;void&gt;

Shares a form with the specified form ID and remote device ID. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.REQUIRE_FORM and ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------- |
| formId | string | Yes | Card ID. |
| deviceId | string | Yes | Remote device ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501003 | The form cannot be operated by the current application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
let deviceId: string = 'EFC11C0C53628D8CC2F8CB5052477E130D075917034613B9884C55CD22B3DEF2';
try {
  formHost.shareForm(formId, deviceId).then(() => {
    console.info('formHost shareForm success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyFormsPrivacyProtected

notifyFormsPrivacyProtected(formIds: Array\<string>, isProtected: boolean, callback: AsyncCallback\<void>): void

Notifies the specified cards of the change in the privacy protection state. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formIds | Array\<string\> | Yes   | List of card IDs whose privacy protection needs to be modified. |
| isProtected | boolean | Yes   | Whether the card is in the privacy protection state.<br>true: The card is in the privacy protection state.<br>false: The card is not in the privacy protection state. |
| callback | AsyncCallback\<void> | Yes | Callback invoked when the privacy protection attribute is set for the specified cards. If the operation is successful, error is undefined; otherwise, error is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsPrivacyProtected(formIds, true, (error: BusinessError) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.notifyFormsPrivacyProtected

notifyFormsPrivacyProtected(formIds: Array\<string\>, isProtected: boolean): Promise\<void\>

Notifies the specified cards of a privacy protection status change. This API uses a promise to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name        | Type            | Mandatory | Description                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formIds     | Array\<string\> | Yes   | List of card IDs whose privacy protection status needs to be changed. |
| isProtected | boolean         | Yes   | Whether the card is in the privacy protection state.<br>true: The card is in the privacy protection state.<br>false: The card is not in the privacy protection state. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formIds: string[] = new Array('12400633174999288', '12400633174999289');
try {
  formHost.notifyFormsPrivacyProtected(formIds, true).then(() => {
    console.info('formHost notifyFormsPrivacyProtected success');
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.acquireFormData<sup>10+</sup>

acquireFormData(formId: string, callback: AsyncCallback\<Record\<string, Object>>): void

Requests the data of the form provider. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| callback | AsyncCallback\<Record\<string, Object>> | Yes   | Callback used to return the API execution result and the data of the form provider. |

**Error codes**

For details about the error codes, see [Common Errors](../errorcode-universal.md) and [Card Errors](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. invalid input parameter during form operation. |

**Example**

```ts
import { formHost } from '@kit.FormKit';

let formId: string = '12400633174999288';
try {
  formHost.acquireFormData(formId, (error: BusinessError, data: Record<string, Object>) => {
    if (error) {
      console.error(`error, code: ${error.code}, message: ${error.message}`);
    } else {
      console.info('formHost acquireFormData success.');
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.acquireFormData<sup>10+</sup>

acquireFormData(formId: string): Promise\<Record\<string, Object>>

Requests the data of the form provider. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name      | Type            | Mandatory | Description                             |
| ----------- | --------------- | ---- | -------------------------------- |
| formId | string | Yes   | Card ID. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise\<Record\<string, Object>> | Promise used to return the result and the data of the form provider. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16500100 | Failed to obtain the configuration information. |
| 16501000 | An internal functional error occurred. invalid input parameter during form operation. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
try {
  formHost.acquireFormData(formId).then((data) => {
    console.info('formHost acquireFormData success' + data);
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (e) {
  console.error(`catch error, code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}
```

## formHost.setRouterProxy<sup>11+</sup>

setRouterProxy(formIds: Array&lt;string&gt;, proxy: Callback&lt;Want&gt;, callback: AsyncCallback&lt;void&gt;): void

Sets the router proxy of a form. This API uses an asynchronous callback to return the Want information required for the form jump.



> **NOTE**
>
>- Generally, for a form added to the home screen, when the form triggers a router jump, the form framework checks whether the jump destination is valid and whether the jump permission is available, and then performs the application jump. If the form host adds a form and sets a router proxy for it, when the form triggers a router jump, the form framework no longer performs the jump. Instead, it returns the want parameter containing the jump destination to the form host. Therefore, if the form host wants to use the want information to perform an application jump, it must ensure that it has the application jump permission. For details, see [UIAbilityContext.startAbility()](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability).
>
>- A formId can have only one router proxy. If the proxy is set multiple times, the last one takes effect.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name     | Type                      | Mandatory | Description                                                         |
| -------- | ------------------------- | --------- | ------------------------------------------------------------ |
| formIds  | Array&lt;string&gt;       | Yes       | Array of card IDs.                                               |
| proxy    | Callback&lt;Want&gt;      | Yes       | Callback function. Returns the Want information required for the jump.                         |
| callback | AsyncCallback&lt;void&gt; | Yes       | Callback function. If the router proxy is set for the specified card successfully, error is undefined; otherwise, an exception is thrown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501003 | The form cannot be operated by the current application.     |

**Example**

```ts
import { common, Want } from '@kit.AbilityKit';
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CardExample {
  @State formId: number = 0;
  @State fwidth: number = 420;
  @State fheight: number = 280;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      FormComponent({
        id: this.formId,
        name: "widget",
        bundle: "com.example.cardprovider",
        ability: "EntryFormAbility",
        module: "entry",
        dimension: FormDimension.Dimension_2_2,
        temporary: false,
      })
        .allowUpdate(true)
        .size({ width: this.fwidth, height: this.fheight })
        .visibility(Visibility.Visible)
        .onAcquired((form) => {
          console.info('testTag onAcquired.');
          this.formId = form.id;
          try {
            let formIds: string[] = [this.formId.toString()];
            formHost.setRouterProxy(formIds, (want: Want) => {
              console.info('formHost recv router event.');
              // The form host handles the jump by itself.
              this.context.startAbility(want, (err: BusinessError) => {
                console.error(`formHost startAbility error, code: ${err.code}, message: ${err.message}`);
              });
            }, (err: BusinessError) => {
              console.error(`set router proxy error, code: ${err.code}, message: ${err.message}`);
            })
          } catch (e) {
            console.error(`formHost setRouterProxy, code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## formHost.setRouterProxy<sup>11+</sup>

setRouterProxy(formIds: Array&lt;string&gt;, proxy: Callback&lt;Want&gt;): Promise&lt;void&gt;

Sets the card redirection proxy. This API uses a promise to return the Want information required for the card redirection.

> **NOTE**
>
>- Generally, for a card added to the home screen, when the card triggers a router redirection, the card framework checks whether the redirection destination is valid and whether the redirection permission is available, and then performs the application redirection. If the form host adds a card and sets a card redirection proxy, when the card triggers a router redirection, the card framework no longer performs the redirection for it. Instead, it returns the Want parameter containing the redirection destination to the form host. Therefore, if the form host wants to use this Want information to perform the application redirection, it must ensure that it has the application redirection permission. For details, see [UIAbilityContext.startAbility()](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#startability).
>
>- A formId can have at most one redirection proxy. If the proxy is set multiple times, the last one set takes effect.



**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name    | Type                 | Mandatory | Description                                 |
| ------- | -------------------- | --------- | ------------------------------------------- |
| formIds | Array&lt;string&gt;  | Yes       | Array of card IDs.                          |
| proxy   | Callback&lt;Want&gt; | Yes       | Callback function. Returns the Want information required for the redirection. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501003 | The form cannot be operated by the current application.     |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { common, Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CardExample {
  @State formId: number = 0;
  @State fwidth: number = 420;
  @State fheight: number = 280;
  private context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      FormComponent({
        id: this.formId,
        name: "widget",
        bundle: "com.example.cardprovider",
        ability: "EntryFormAbility",
        module: "entry",
        dimension: FormDimension.Dimension_2_2,
        temporary: false,
      })
        .allowUpdate(true)
        .size({ width: this.fwidth, height: this.fheight })
        .visibility(Visibility.Visible)
        .onAcquired((form) => {
          console.info('testTag onAcquired.');
          this.formId = form.id;
          try {
            let formIds: string[] = [this.formId.toString()];
            formHost.setRouterProxy(formIds, (want: Want) => {
              console.info('formHost recv router event.');
              // Handle the redirection by the form host itself.
              this.context.startAbility(want, (err: BusinessError) => {
                console.error(`formHost startAbility error, code: ${err.code}, message: ${err.message}`);
              });
            }).then(() => {
              console.info('formHost set router proxy success');
            }).catch((err: BusinessError) => {
              console.error(`set router proxy error, code: ${err.code}, message: ${err.message}`);
            })
          } catch (e) {
            console.error(`formHost setRouterProxy, code: ${e.code}, message: ${e.message}`);
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## formHost.clearRouterProxy<sup>11+</sup>

clearRouterProxy(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Clears the router proxy of a card. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name     | Type                      | Mandatory | Description                                                         |
| -------- | ------------------------- | --------- | ------------------------------------------------------------ |
| formIds  | Array&lt;string&gt;      | Yes       | Array of card IDs.                                               |
| callback | AsyncCallback&lt;void&gt; | Yes       | Callback invoked when the router proxy of the specified card is cleared successfully. In this case, **error** is **undefined**; otherwise, an exception is thrown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501003 | The form cannot be operated by the current application.     |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.clearRouterProxy(formIds, (err: BusinessError) => {
    if (err) {
      console.error(`formHost clear router proxy error, code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.clearRouterProxy<sup>11+</sup>

clearRouterProxy(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Clears the router proxy of a card. This API uses a promise to return the result.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name    | Type              | Mandatory | Description          |
| ------- | ------------------- | ---- | -------------- |
| formIds | Array&lt;string&gt; | Yes  | Array of card IDs. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501003 | The form cannot be operated by the current application.     |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.clearRouterProxy(formIds).then(() => {
    console.info('formHost clear router proxy success');
  }).catch((err: BusinessError) => {
    console.error(`formHost clear router proxy error, code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
## formHost.setFormsRecyclable<sup>11+</sup>

setFormsRecyclable(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Sets the forms to be recyclable. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name     | Type                      | Mandatory | Description                                                         |
| -------- | ------------------------- | --------- | ------------------------------------------------------------ |
| formIds  | Array&lt;string&gt;      | Yes       | Array of card IDs.                                               |
| callback | AsyncCallback&lt;void&gt; | Yes       | Callback invoked to return the result. If the forms are set to be recyclable successfully, **error** is **undefined**; otherwise, an exception is thrown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | caller is not system app.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.setFormsRecyclable(formIds, (err: BusinessError) => {
    if (err) {
      console.error(`setFormsRecyclable error, code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.setFormsRecyclable<sup>11+</sup>

setFormsRecyclable(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Sets the forms to be recyclable. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name    | Type                | Mandatory | Description            |
| ------- | ------------------- | --------- | ---------------------- |
| formIds | Array&lt;string&gt; | Yes       | Array of card IDs. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | caller is not system app.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.setFormsRecyclable(formIds).then(() => {
    console.info('setFormsRecyclable success');
  }).catch((err: BusinessError) => {
    console.error(`setFormsRecyclable error, code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
## formHost.recoverForms<sup>11+</sup>

recoverForms(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;void&gt;): void

Recovers a recycled form and updates its status to non-recyclable. If the form has not been recycled, only its status is updated to non-recyclable. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name     | Type                      | Mandatory | Description                                                         |
| -------- | ------------------------- | --------- | ------------------------------------------------------------ |
| formIds  | Array&lt;string&gt;      | Yes       | Array of card IDs.                                               |
| callback | AsyncCallback&lt;void&gt; | Yes       | Callback invoked when the form is recovered successfully. In this case, error is undefined; otherwise, an exception is thrown. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | caller is not system app.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.recoverForms(formIds, (err: BusinessError) => {
    if (err) {
      console.error(`recoverForms error, code: ${err.code}, message: ${err.message}`);
    }
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
## formHost.recoverForms<sup>11+</sup>

recoverForms(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Recovers a recycled form and updates its state to non-recoverable. If the form has not been recycled, only its state is updated to non-recoverable. This API uses a promise to return the result asynchronously.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name    | Type                | Mandatory | Description        |
| ------- | ------------------- | --------- | ------------------ |
| formIds | Array&lt;string&gt; | Yes       | Array of card IDs. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | caller is not system app.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.recoverForms(formIds).then(() => {
    console.info('formHost recoverForms success');
  }).catch((err: BusinessError) => {
    console.error(`formHost recover forms error, code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error(`catch error, code: ${e.code}, message: ${e.message}`);
}
```
## formHost.recycleForms<sup>12+</sup>

recycleForms(formIds: Array&lt;string&gt;): Promise&lt;void&gt;

Recycles the card memory immediately. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name    | Type                | Mandatory | Description          |
| ------- | ------------------- | --------- | -------------------- |
| formIds | Array&lt;string&gt; | Yes       | Array of card IDs. |

**Return value**

| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                 |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formIds: string[] = ['12400633174999288'];
  formHost.recycleForms(formIds).then(() => {
    console.info('recycle forms success');
  }).catch((err: BusinessError) => {
    console.error(`formHost recycle forms error, code: ${err.code}, message: ${err.message}`);
  });
} catch (e) {
  console.error(`catch error, code: ${e.code}, message: ${e.message}`);
}
```

## formHost.updateFormLocation<sup>12+</sup>
updateFormLocation(formId: string, location: formInfo.FormLocation): void;

Updates the card location.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------- |
| formId | string | Yes | Card ID. |
| location |[formInfo.FormLocation](js-apis-app-form-formInfo-sys.md#formlocation12) | Yes | Card location. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | caller is not system app.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501001 | The ID of the form to be operated does not exist.            |
| 16501003 | The form cannot be operated by the current application.     |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  formHost.updateFormLocation(formId, formInfo.FormLocation.SCREEN_LOCK);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.setPublishFormResult<sup>12+</sup>

setPublishFormResult(formId: string, result: formInfo.PublishFormResult): void;

Sets the result of adding a form to the home screen.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type                                                         | Mandatory | Description               |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| formId | string                                                       | Yes  | Card ID.         |
| result | [formInfo.PublishFormResult](js-apis-app-form-formInfo-sys.md#publishformresult12) | Yes  | Result of publishing the form to the home screen. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | The application is not a system application.                                    |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501001 | The ID of the form to be operated does not exist.            |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  let res: formInfo.PublishFormResult = { code: formInfo.PublishFormErrorCode.SUCCESS, message: '' };
  formHost.setPublishFormResult(formId, res);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.updateFormLockedState<sup>22+</sup>

updateFormLockedState(formId: string, isLocked: boolean): Promise&lt;void&gt;

Notifies the card framework of a card control state update. This API uses a promise to return the result asynchronously.

The card control state means that when an application enables application lock control, the cards of the corresponding application also follow the application lock control. In this case, the card page is masked with a locked mask style. In the control state, a password set when the lock is enabled is required to operate and use the card.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type | Mandatory | Description |
|-------|------|------|-----|
| formId | string | Yes | Card ID. |
| isLocked | boolean | Yes | Whether the card is in the control state. The value **true** indicates the control state, and **false** indicates the non-control state. |

**Return value**
| Type                | Description                      |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permissions denied.                                          |
| 202      | caller is not a system app.                 |
| 16500050 | IPC connection error.                            |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred.                       |
| 16501001 | The ID of the form to be operated does not exist.                       |
| 16501003 | The form cannot be operated by the current application.     |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let formId: string = '12400633174999288';
let isLocked: boolean = true;

try {
  formHost.updateFormLockedState(formId, isLocked).then(() => {
    console.info(`formHost updateFormLockedState success`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.addForm<sup>12+</sup>

addForm(want: Want): Promise&lt;formInfo.RunningFormInfo&gt;

Adds a theme form. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | Want information carried when querying the form status. It must contain the bundle name, ability name, module name, form name, form dimension, and so on. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[formInfo.RunningFormInfo](js-apis-app-form-formInfo.md#runningforminfo20)&gt; | Promise object. Returns the form information that meets the conditions, including the form name, dimension, and so on. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let want: Want = {
    'bundleName': 'com.huawei.hmsapp.thememanager',
    'abilityName': 'ThemeFaCardUIExtAbility',
    'parameters': {
      'ohos.extra.param.key.form_dimension': 4,
      'ohos.extra.param.key.form_is_theme': true,
      'ohos.extra.param.key.form_location': 0,
      'ohos.extra.param.key.module_name': 'entry',
      'ohos.extra.param.key.form_name': 'widget',
      'themeFormId': '0',
      'themeId': '2181824853'
    }
  };
  formHost.addForm(want).then((data: formInfo.RunningFormInfo) => {
    console.info(`formHost addForm, formId: ${data.formId}`);
  }).catch((error: BusinessError) => {
    console.error(`formHost addForm error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.on('formOverflow')<sup>20+</sup>

on(type: 'formOverflow', callback: Callback&lt;formInfo.OverflowRequest&gt;): void

Subscribes to the interactive form animation request event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type       | Mandatory | Description |
|----------|--------|---|---------------------------------------|
| type     | string | Yes | Event callback type. The supported event is 'formOverflow', which indicates an interactive form animation request. |
| callback | Callback&lt;[formInfo.OverflowRequest](js-apis-app-form-formInfo-sys.md#overflowrequest20)&gt; | Yes | Callback invoked when the form host processes the animation request. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                                  |
|-------|-----------------------------------------------------------------------------------------------------------|
| 202   | The application is not a system application.                                                              |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.on('formOverflow', (request: formInfo.OverflowRequest) => {
    console.info(`formHost on formOverflow, formId is ${request.formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.off('formOverflow')<sup>20+</sup>

off(type: 'formOverflow', callback?: Callback&lt;formInfo.OverflowRequest&gt;): void

Unsubscribes from the interactive form animation effect request event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description                                     |
| ------ | ------ |----|----------------------------------------|
| type | string | Yes  | Event callback type. The supported event is 'formOverflow', which indicates an interactive form animation effect request. |
| callback |Callback&lt;[formInfo.OverflowRequest](js-apis-app-form-formInfo-sys.md#overflowrequest20)&gt; | No  | Callback for the subscribed interactive form animation effect request event. If this parameter is left unspecified, all registered callbacks for the interactive form animation effect request event are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                                |
| --- |-----------------------------------------------------------------------------------------------------------|
| 202 | The application is not a system application.                                                              |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('formOverflow', (request: formInfo.OverflowRequest) => {
    console.info(`formHost off formOverflow, formId is ${request.formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.on('changeSceneAnimationState')<sup>20+</sup>

on(type: 'changeSceneAnimationState', callback: Callback&lt;formInfo.ChangeSceneAnimationStateRequest&gt;): void

Subscribes to the state switch request event of an interactive form. The state of an interactive form is classified into the active state and the inactive state. In the inactive state, an interactive form behaves the same as a normal form. In the active state, an interactive form supports starting the LiveFormExtensionAbility process developed by the form provider to implement the dynamic effects of the interactive form. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description                                                   |
| ------ | ------ | ---- |------------------------------------------------------|
| type | string | Yes   | Event callback type. The supported event is 'changeSceneAnimationState', which indicates the state switch of an interactive form.|
| callback |Callback&lt;[formInfo.ChangeSceneAnimationStateRequest](js-apis-app-form-formInfo-sys.md#changesceneanimationstaterequest20)&gt; | Yes | Callback invoked when the form host handles the state switch request.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                                  |
|-------|-----------------------------------------------------------------------------------------------------------|
| 202   | The application is not a system application.                                                              |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.on('changeSceneAnimationState', (request: formInfo.ChangeSceneAnimationStateRequest): void => {
    console.info(`formHost on changeSceneAnimationState, formId is ${request.formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.off('changeSceneAnimationState')<sup>20+</sup>

off(type: 'changeSceneAnimationState', callback?: Callback&lt;formInfo.ChangeSceneAnimationStateRequest&gt;): void

Unsubscribes from the interactive form state switch request event. The interactive form state is divided into the active state and the inactive state. In the inactive state, the interactive form behaves the same as a normal form; in the active state, the interactive form supports starting the LiveFormExtensionAbility process developed by the form provider to implement interactive form animation effects. This API uses an asynchronous callback.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ |----| ------- |
| type | string | Yes  | Event callback type. The supported event is 'changeSceneAnimationState', which indicates the interactive form state switch.|
| callback |Callback&lt;[formInfo.ChangeSceneAnimationStateRequest](js-apis-app-form-formInfo-sys.md#changesceneanimationstaterequest20)&gt; | No  | Callback for the interactive form state switch request event. If this parameter is left unspecified, all registered callbacks for the interactive form state switch event are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('changeSceneAnimationState', (request: formInfo.ChangeSceneAnimationStateRequest): void => {
    console.info(`formHost off changeSceneAnimationState, formId is ${request.formId}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.on('getFormRect')<sup>20+</sup>

on(type: 'getFormRect', callback: formInfo.GetFormRectInfoCallback): void

Subscribes to the card position and size query request event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description                                                   |
| ------ | ------ | ---- |------------------------------------------------------|
| type | string | Yes   | Event callback type. The supported event is 'getFormRect', which indicates a card position and size query.|
| callback |[formInfo.GetFormRectInfoCallback](js-apis-app-form-formInfo-sys.md#getformrectinfocallback20) | Yes | Callback function. The form host processes the query request and returns the position information of the card relative to the upper left corner of the screen and the card size information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                                  |
|-------|-----------------------------------------------------------------------------------------------------------|
| 202   | The application is not a system application.                                                              |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.on('getFormRect', (formId: string): Promise<formInfo.Rect> => {
    // The form host needs to process the query request, calculate and return the card size and position information.
    return new Promise<formInfo.Rect>((resolve: Function) => {
      console.info(`formHost on getFormRect, formId is ${formId}`);
      let formRect: formInfo.Rect = {
        left: 0,
        top: 0,
        width: 0,
        height: 0
      };
      resolve(formRect);
    })
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.off('getFormRect')<sup>20+</sup>

off(type: 'getFormRect', callback?: formInfo.GetFormRectInfoCallback): void

Unsubscribes from the form position and size query request event. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ |----| ------- |
| type | string | Yes  | Event callback type. The supported event is 'getFormRect', which indicates a form position and size query.|
| callback |[formInfo.GetFormRectInfoCallback](js-apis-app-form-formInfo-sys.md#getformrectinfocallback20) | No  | Callback for the subscribed form position and size query request. If this parameter is left unspecified, all registered callbacks for the form position and size query event are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('getFormRect');
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.updateFormSize<sup>20+</sup>

updateFormSize(formId: string, newDimension: formInfo.FormDimension, newRect: formInfo.Rect): void

Adjusts the form size.

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| formId | string | Yes   | Card ID. |
| newDimension | [formInfo.FormDimension](js-apis-app-form-formInfo.md#formdimension) | Yes | Form size, for example, Dimension_1_2, which indicates a 1 x 2 form. |
| newRect | [formInfo.Rect](js-apis-app-form-formInfo.md#rect20) | Yes | Form position information, including the x and y coordinates of the upper-left vertex of the form and the width and height of the form. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | caller is not system app. |
| 16501000 | An internal functional error occurred. |
| 16501001 | The ID of the form to be operated does not exist. |
| 16501012 | The dimension parameter is incorrect. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let formId: string = '12400633174999288';
  let newDimension = formInfo.FormDimension.Dimension_1_2;
  let newRect: formInfo.Rect = {
    left: 1,
    top: 2,
    width: 100,
    height: 100
  };
  formHost.updateFormSize(formId, newDimension, newRect);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.on('getLiveFormStatus')<sup>20+</sup>

on(type: 'getLiveFormStatus', callback: formInfo.GetLiveFormStatusCallback): void

Subscribes to the running status query event of all live forms. This API uses an asynchronous callback to return the result.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description                                                   |
| ------ | ------ | ---- |------------------------------------------------------|
| type | string | Yes   | Event callback type. The supported event is 'getLiveFormStatus', which indicates the online form status query.|
| callback |[formInfo.GetLiveFormStatusCallback](js-apis-app-form-formInfo-sys.md#getliveformstatuscallback20) | Yes | Callback function. The form host processes the query request and returns the running status of all live forms.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.on('getLiveFormStatus', (): Record<string, string> => {
    // The form host processes the query request, calculates, and returns the status information.
    return { "status": "active" };
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.off('getLiveFormStatus')<sup>20+</sup>

off(type: 'getLiveFormStatus', callback?: formInfo.GetLiveFormStatusCallback): void

Unsubscribes from the running status query event of all live forms. This API uses an asynchronous callback.

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description                                                   |
| ------ | ------ | ---- |------------------------------------------------------|
| type | string | Yes   | Type of the event callback. The supported event is 'getLiveFormStatus', which indicates the form position and size query.|
| callback |[formInfo.GetLiveFormStatusCallback](js-apis-app-form-formInfo-sys.md#getliveformstatuscallback20) | Yes | Callback for the form position and size query event. If this parameter is left unspecified, all callbacks for the running status query event of live forms are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 202 | The application is not a system application. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.off('getLiveFormStatus', (): Record<string, string> => {
    // The form host needs to process the query request, calculate and return the status information.
    return { "status": "inactive" };
  });
} catch (error) {
  console.error(`catch error, code: ${error.code}, message: ${error.message}`);
}
```

## formHost.getAllTemplateFormsInfo<sup>23+</sup>

getAllTemplateFormsInfo(): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains the template form information provided by all applications on the device. This API uses a promise to return the result asynchronously.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Return value**

| Type                                                                                     | Description                    |
|:---------------------------------------------------------------------------------------|:----------------------|
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Promise used to return the retrieved form information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.getAllTemplateFormsInfo().then((data: formInfo.FormInfo[]) => {
    for (let info of data) {
      console.info(`getAllTemplateFormsInfo bundleName: ${info.bundleName}, moduleName: ${info.moduleName}, name: ${info.name}`);
    }
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## formHost.getTemplateFormsInfo<sup>23+</sup>

getTemplateFormsInfo(bundleName: string, moduleName?: string): Promise&lt;Array&lt;formInfo.FormInfo&gt;&gt;

Obtains the template form information provided by a specified application on the device. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| bundleName | string | Yes | Bundle name of the application to query. |
| moduleName | string | No |  Name of the module to query. If this parameter is left empty, the default value is used. |

**Return value**

| Type                                                                                     | Description                                |
|:---------------------------------------------------------------------------------------| :---------------------------------- |
| Promise&lt;Array&lt;[formInfo.FormInfo](js-apis-app-form-formInfo.md#forminfo)&gt;&gt; | Promise used to return the card information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.getTemplateFormsInfo('com.example.ohos.formjsdemo', 'entry').then((data: formInfo.FormInfo[]) => {
    for (let info of data) {
      console.info(`getTemplateFormsInfo bundleName: ${info.bundleName}, moduleName: ${info.moduleName}, name: ${info.name}`);
    }
  }).catch((error: BusinessError) => {
    console.error(`error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.onTemplateFormDetailInfoChange<sup>23+</sup>

onTemplateFormDetailInfoChange(callback: formInfo.TemplateFormDetailInfoCallback): void

Subscribes to changes in the static configuration information of template forms. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.TemplateFormDetailInfoCallback](js-apis-app-form-formInfo-sys.md#templateformdetailinfocallback23) | Yes   | Callback invoked when the static configuration information of a template form changes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback: formInfo.TemplateFormDetailInfoCallback = (info: formInfo.TemplateFormDetailInfo[]) => {
    for (let templateFormDetailInfo of info) {
      console.info(`TemplateFormDetailInfoCallback bundleName: ${templateFormDetailInfo.bundleName}, moduleName: ${templateFormDetailInfo.moduleName}, formName: ${templateFormDetailInfo.formName}`);
    }
  };
  formHost.onTemplateFormDetailInfoChange(callback);
  console.info(`onTemplateFormDetailInfoChange success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```


## formHost.offTemplateFormDetailInfoChange<sup>23+</sup>

offTemplateFormDetailInfoChange(callback?: formInfo.TemplateFormDetailInfoCallback): void

Unsubscribes from changes to the static configuration information of a template form. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.TemplateFormDetailInfoCallback](js-apis-app-form-formInfo-sys.md#templateformdetailinfocallback23) | No   | Callback for the change event of the static configuration information of a template form. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.offTemplateFormDetailInfoChange();
  console.info(`offTemplateFormDetailInfoChange success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.getFormIdsByFormLocation<sup>24+</sup>

getFormIdsByFormLocation(location: formInfo.FormLocation): Promise&lt;Array&lt;string&gt;&gt;

Obtains the list of card IDs at the specified card location on the device. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| location | [formInfo.FormLocation](js-apis-app-form-formInfo-sys.md#formlocation12) | Yes | Card location. |

**Return value**

| Type                                                                                     | Description                                |
|:---------------------------------------------------------------------------------------| :---------------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the list of card IDs retrieved. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |
| 16501016 | The location of the widget is invalid. |

**Example**

```ts
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

## formHost.onGetWantParamsCallback

onGetWantParamsCallback(callback: formInfo.GetWantParamsCallback): void

Subscribes to the event of obtaining card parameters. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.GetWantParamsCallback](js-apis-app-form-formInfo-sys.md#getwantparamscallback) | Yes   | Callback invoked to return the card parameter information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback = (formInfos: formInfo.FormInfo[]): Array<Record<string, Object>> => {
    console.info(`onGetWantParamsCallback formInfos length: ${formInfos.length}`);
    let wantParamsList: Array<Record<string, Object>> = [];
    for (let formInfoItem of formInfos) {
      let wantParams: Record<string, Object> = {};
      wantParams['key'] = 'value';
      wantParamsList.push(wantParams);
    }
    return wantParamsList;
  };
  formHost.onGetWantParamsCallback(callback);
  console.info(`onGetWantParamsCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.offGetWantParamsCallback

offGetWantParamsCallback(callback?: formInfo.GetWantParamsCallback): void

Unsubscribes from the event of obtaining card parameters. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.GetWantParamsCallback](js-apis-app-form-formInfo-sys.md#getwantparamscallback) | No   | Callback for the card parameter event. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.offGetWantParamsCallback();
  console.info(`offGetWantParamsCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.onUpdateFormsConfigCallback

onUpdateFormsConfigCallback(callback: formInfo.UpdateFormsConfigCallback): void

Subscribes to the form configuration update event. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.UpdateFormsConfigCallback](js-apis-app-form-formInfo-sys.md#updateformsconfigcallback) | Yes   | Callback invoked to return the form configuration update information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback = (configInfo: formInfo.FormCustomConfig[]): void => {
    console.info(`onUpdateFormsConfigCallback configInfo length: ${configInfo.length}`);
    for (let config of configInfo) {
      console.info(`bundleName: ${config.bundleName}, moduleName: ${config.moduleName}`);
    }
  };
  formHost.onUpdateFormsConfigCallback(callback);
  console.info(`onUpdateFormsConfigCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.offUpdateFormsConfigCallback

offUpdateFormsConfigCallback(callback?: formInfo.UpdateFormsConfigCallback): void

Unsubscribes from the form configuration update event. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.UpdateFormsConfigCallback](js-apis-app-form-formInfo-sys.md#updateformsconfigcallback) | No   | Callback for the form configuration update event.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.offUpdateFormsConfigCallback();
  console.info(`offUpdateFormsConfigCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.onDeleteFormsCallback

onDeleteFormsCallback(callback: formInfo.DeleteFormsCallback): void

Subscribes to the form deletion event. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.DeleteFormsCallback](js-apis-app-form-formInfo-sys.md#deleteformscallback) | Yes   | Callback invoked to return the list of IDs of the deleted forms. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback = (formIds: string[]): void => {
    console.info(`onDeleteFormsCallback formIds length: ${formIds.length}`);
    for (let formId of formIds) {
      console.info(`deleted formId: ${formId}`);
    }
  };
  formHost.onDeleteFormsCallback(callback);
  console.info(`onDeleteFormsCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.offDeleteFormsCallback

offDeleteFormsCallback(callback?: formInfo.DeleteFormsCallback): void

Unsubscribes from the form deletion event. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.DeleteFormsCallback](js-apis-app-form-formInfo-sys.md#deleteformscallback) | No   | Callback for the form deletion event, which returns the list of deleted card IDs.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.offDeleteFormsCallback();
  console.info(`offDeleteFormsCallback success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.registerFormHostService

registerFormHostService(service: formInfo.FormHostServiceInfo): Promise&lt;string&gt;

Registers the form host service information. After successful registration, the information can be used for cross-device form publishing. This API uses a promise to return the result asynchronously.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Since:** 26.0.1

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | -------|
| service | [formInfo.FormHostServiceInfo](js-apis-app-form-formInfo-sys.md#formhostserviceinfo) | Yes | Form host service information to be registered with the card management service. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;string&gt; | Promise used to return the service ID of the successfully registered form host service. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let service: formInfo.FormHostServiceInfo = {
  serviceName: 'serviceName',
  serviceDisplayName: 'serviceDisplayName',
  displayId: '0'
};
try {
  formHost.registerFormHostService(service).then((data: string) => {
    console.info(`formHost registerFormHostService success, service ID is: ${data}`);
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.unregisterFormHostService

unregisterFormHostService(serviceId: string): Promise&lt;void&gt;

Unregisters the form host service information. After unregistration, the corresponding form host service cannot be used for cross-device form publishing. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**System API**: This is a system API.

**Since:** 26.0.1

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | -------|
| serviceId | string | Yes | Service ID of the form host service to be unregistered.|

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Card Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permissions denied. |
| 202 | The application is not a system application. |
| 16500050 | IPC connection error. |
| 16501019 | A form service not owned by you cannot be unregistered. |
| 16501000 | An internal functional error occurred. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

let serviceId: string = 'serviceId'; // Service ID of the form host service to be unregistered. Replace it with the actual service ID.
try {
  formHost.unregisterFormHostService(serviceId).then(() => {
    console.info('formHost unregisterFormHostService success');
  }).catch((error: BusinessError) => {
    console.error(`promise error, code: ${error.code}, message: ${error.message}`);
  });
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.onGetVisibleFormRect

onGetVisibleFormRect(callback: formInfo.GetFormRectInfoCallback): void

Subscribes to the event of requesting the position and size of a visible form. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.GetFormRectInfoCallback](js-apis-app-form-formInfo-sys.md#getformrectinfocallback20) | Yes   | Callback invoked to return the position of the form relative to the upper left corner of the screen and the size of the form, in vp. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |

**Example**

```ts
import { formHost, formInfo } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const callback = (formId: string): Promise<formInfo.Rect> => {
    // The form host processes the query request, calculates and returns the size and position of the form.
    return new Promise<formInfo.Rect>((resolve: Function) => {
      console.info(`formHost onGetVisibleFormRect, formId is ${formId}`);
      let formRect: formInfo.Rect = {
        left: 0,
        top: 0,
        width: 0,
        height: 0
      };
      resolve(formRect);
    })
  };
  formHost.onGetVisibleFormRect(callback);
  console.info(`formHost onGetVisibleFormRect success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```

## formHost.offGetVisibleFormRect

offGetVisibleFormRect(callback?: formInfo.GetFormRectInfoCallback): void

Unsubscribes from the event of requesting the position and size of a visible form. This API uses an asynchronous callback to return the result.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.Ability.Form

**Parameters**

| Name | Type    | Mandatory | Description    |
| ------ | ------ | ---- | ------- |
| callback | [formInfo.GetFormRectInfoCallback](js-apis-app-form-formInfo-sys.md#getformrectinfocallback20) | No   | Callback for the subscribed event of requesting the position and size of a visible form. If this parameter is left unspecified, all registered callbacks for the event of requesting the position and size of a visible form are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Form Error Codes](errorcode-form.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 16500050 | IPC connection error. |
| 16500060 | Service connection error. |

**Example**

```ts
import { formHost } from '@kit.FormKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  formHost.offGetVisibleFormRect();
  console.info(`formHost offGetVisibleFormRect success`);
} catch (error) {
  console.error(`catch error, code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`);
}
```
