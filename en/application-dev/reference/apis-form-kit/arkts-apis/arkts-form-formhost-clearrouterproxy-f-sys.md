# clearRouterProxy (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

<a id="clearrouterproxy1"></a>

## clearRouterProxy

```TypeScript
function clearRouterProxy(formIds: Array<string>, callback: AsyncCallback<void>): void
```

Clears the router proxy set for widgets. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function clearRouterProxy(formIds: Array<string>, callback: AsyncCallback<void>): void--><!--Device-formHost-function clearRouterProxy(formIds: Array<string>, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | Array of widget IDs. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the router proxy is cleared, **error** is **undefined**; otherwise, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501003](../errorcode-form.md#16501003-widget-not-operatable) | The form cannot be operated by the current application. |

<!--Del-->
**Examples**

```TypeScript
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

<!--DelEnd-->


<a id="clearrouterproxy2"></a>

## clearRouterProxy

```TypeScript
function clearRouterProxy(formIds: Array<string>): Promise<void>
```

Clears the router proxy set for widgets. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.REQUIRE_FORM

<!--Device-formHost-function clearRouterProxy(formIds: Array<string>): Promise<void>--><!--Device-formHost-function clearRouterProxy(formIds: Array<string>): Promise<void>-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | Array of widget IDs. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permissions denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not a system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types; 3.Parameter verification failed. |
| [16500050](../errorcode-form.md#16500050-ipc-failure) | IPC connection error. |
| [16500060](../errorcode-form.md#16500060-service-connection-failure) | Service connection error. |
| [16501000](../errorcode-form.md#16501000-internal-function-error) | An internal functional error occurred. |
| [16501003](../errorcode-form.md#16501003-widget-not-operatable) | The form cannot be operated by the current application. |

<!--Del-->
**Examples**

```TypeScript
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

<!--DelEnd-->
