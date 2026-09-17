# setRouterProxy (System API)

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## setRouterProxy

```TypeScript
function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>, callback: AsyncCallback<void>): void
```

Sets a router proxy for widgets and obtains the Want information required for redirection. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> Generally, for a widget added to the home screen, in the case of router-based redirection, the widget framework
> checks whether the destination is proper and whether the widget has the redirection permission, and then
> triggers redirection accordingly. For a widget that is added to a widget host and has a router proxy configured,
> in the case of router-based redirection, the widget framework does not trigger redirection for the widget.
> - Only one router proxy can be set for a widget. If multiple proxies are set, only the last proxy takes effect.

**Since:** 11

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | Array of widget IDs. |
| proxy | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Callback used to return the Want information required for redirection. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the router proxy is set, **error** is **undefined**; otherwise, an exception is thrown. |

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


## setRouterProxy

```TypeScript
function setRouterProxy(formIds: Array<string>, proxy: Callback<Want>): Promise<void>
```

Sets a router proxy for widgets and obtains the Want information required for redirection. This API uses a promise to return the result. This API uses a promise to return the result.

> **NOTE:** 
> 
> - Generally, for a widget added to the home screen, in the case of router-based redirection, the widget framework checks whether the destination is proper and whether the widget has the redirection permission, and then triggers redirection accordingly. For a widget that is added to a widget host and has a router proxy configured,in the case of router-based redirection, the widget framework does not trigger redirection for the widget.
> 
> - Only one router proxy can be set for a widget. If multiple proxies are set, only the last proxy takes effect.

**Since:** 11

**Required permissions:** ohos.permission.REQUIRE_FORM

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| formIds | Array&lt;string&gt; | Yes | Array of widget IDs. |
| proxy | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Callback used to return the Want information required for redirection. |

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
