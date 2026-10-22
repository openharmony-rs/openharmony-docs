# InputMethodExtensionContext (System API)

```TypeScript
declare class InputMethodExtensionContext extends ExtensionContext
```

The **@ohos.InputMethodExtensionContext** module is the context of **InputMethodExtensionAbility**, inherited from **ExtensionContext**, and provides context-level operation APIs for input method extension capabilities. <br> <br>This module is the context class of the input method **ExtensionAbility**, inherited from **ExtensionContext**, and is provided as the **context** property of an **InputMethodExtensionAbility** instance. It carries the context capabilities that an input method extension app can use during its lifecycle, including destroying itself and starting other apps. <br> <br>This module provides two core capabilities: (1) destroying the input method ExtensionAbility through **destroy()** to terminate the lifecycle of the input method app; (2) starting the target app through **startAbility()** so that the input method app can launch other abilities for interaction, expanding the flexibility and extensibility of input method features. <br> <br>Use this module when you develop an input method ExtensionAbility and need to perform context-level operations during its lifecycle. Typical scenarios include: the input method app actively destroys itself in the **onDestroy** callback, and the input method app needs to start the settings page or other auxiliary apps. <br> <br>The core APIs in this module are divided into two categories by feature: <br> <br>1. Lifecycle management: **destroy()** is used to destroy the input method ExtensionAbility and terminate the input method app.
2. Ability interaction: **startAbility()** is used to start a target ability (such as a settings page) from the input method app,
extending the interaction between the input method app and other apps. <br> <br>Typical usage process: obtain **this.context** in the **onCreate** callback of **InputMethodExtensionAbility** → call **context.destroy()** when the input method needs to be terminated → call **context.startAbility(want)** when another app needs to be started. <br> Name | Description |

|---|---|  
| InputMethodExtensionContext | Input method extension context class inherited from **ExtensionContext**, which provides context‑level operation capabilities for **InputMethodExtensionAbility**. Key methods include: **destroy()** for destroying the input method itself (supports both callback‑based and promise‑based asynchronous modes), and **startAbility(want)** for starting a target app (promise‑based, added since API version 12). | <br> <br>The **InputMethodExtensionContext** of this module must be obtained from a child class instance of **InputMethodExtensionAbility**. Its APIs are used in combination with the lifecycle callbacks of **InputMethodExtensionAbility**. <br> <br>  
> **NOTE:** <br>
> <br>
> The `InputMethodExtensionContext` instance is obtained through the `this.context` property of an <br>
> `InputMethodExtensionAbility` child class and cannot be created directly. `destroy()` is usually called in the <br>
> `onDestroy` lifecycle callback, and you can also proactively call it at other times to terminate the input method <br>
> ExtensionAbility.

**Inheritance/Implementation:** InputMethodExtensionContext extends [ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md)

**Since:** 9

<!--Device-unnamed-declare class InputMethodExtensionContext extends ExtensionContext--><!--Device-unnamed-declare class InputMethodExtensionContext extends ExtensionContext-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

## Modules to Import

```TypeScript
import { InputMethodExtensionContext } from '@kit.IMEKit';
```

## connectAbility

```TypeScript
connectAbility(want: Want, options: ConnectOptions): number
```

Connects this ability to a ServiceExtensionAbility.

**Since:** 9

**Deprecated since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-connectAbility(want: Want, options: ConnectOptions): number--><!--Device-InputMethodExtensionContext-connectAbility(want: Want, options: ConnectOptions): number-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability, such as the ability name and bundle name. |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-i.md) | Yes | Callback used to return the information indicating that the connection is successful, interrupted, or failed. |

**Return value:**

| Type | Description |
| --- | --- |
| number | A number, based on which the connection will be interrupted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 10 and later |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed.<br>**Applicable version:** 10 and later |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires.<br>**Applicable version:** 10 and later |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI.<br>**Applicable version:** 10 and later |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out.<br>**Applicable version:** 10 and later |

## connectAbilityWithAccount

```TypeScript
connectAbilityWithAccount(want: Want, accountId: number): number
```

Connects to a ServiceExtensionAbility with a specified account.

**Since:** 9

**Deprecated since:** 10

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-connectAbilityWithAccount(want: Want, accountId: number): number--><!--Device-InputMethodExtensionContext-connectAbilityWithAccount(want: Want, accountId: number): number-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability. |
| accountId | number | Yes | ID of the target system account. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Result code of the connection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 10 and later |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed.<br>**Applicable version:** 10 and later |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires.<br>**Applicable version:** 10 and later |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI.<br>**Applicable version:** 10 and later |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out.<br>**Applicable version:** 10 and later |

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

Connects this ability to a ServiceExtensionAbility.

**Since:** 9

**Deprecated since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): number--><!--Device-InputMethodExtensionContext-connectServiceExtensionAbility(want: Want, options: ConnectOptions): number-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability, such as the ability name and bundle name. |
| options | [ConnectOptions](../../apis-ability-kit/arkts-apis/arkts-ability-connectoptions-i.md) | Yes | Callback used to return the information indicating that the connection is successful, interrupted, or failed. |

**Return value:**

| Type | Description |
| --- | --- |
| number | A number, based on which the connection will be interrupted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type.<br>**Applicable version:** 10 and later |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component.<br>**Applicable version:** 10 and later |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed.<br>**Applicable version:** 10 and later |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires.<br>**Applicable version:** 10 and later |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI.<br>**Applicable version:** 10 and later |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out.<br>**Applicable version:** 10 and later |

## disconnectAbility

```TypeScript
disconnectAbility(connection: number, callback: AsyncCallback<void>): void
```

Disconnects this ability from a ServiceExtensionAbility and after the successful disconnection, sets the remote object returned upon the connection to void. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-disconnectAbility(connection: number, callback: AsyncCallback<void>): void--><!--Device-InputMethodExtensionContext-disconnectAbility(connection: number, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | Number returned after **connectServiceExtensionAbility** is called. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If disconnection is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

## disconnectAbility

```TypeScript
disconnectAbility(connection: number): Promise<void>
```

Disconnects this ability from a ServiceExtensionAbility and after the successful disconnection, sets the remote object returned upon the connection to void. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-disconnectAbility(connection: number): Promise<void>--><!--Device-InputMethodExtensionContext-disconnectAbility(connection: number): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | Number returned after **connectServiceExtensionAbility** is called. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void
```

Disconnects this ability from a ServiceExtensionAbility and after the successful disconnection, sets the remote object returned upon the connection to void. This API can be called only on the main thread. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void--><!--Device-InputMethodExtensionContext-disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | Number returned after **connectServiceExtensionAbility** is called. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If disconnection is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

Disconnects this ability from a ServiceExtensionAbility and after the successful disconnection, sets the remote object returned upon the connection to void. This API can be called only on the main thread. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-disconnectServiceExtensionAbility(connection: number): Promise<void>--><!--Device-InputMethodExtensionContext-disconnectServiceExtensionAbility(connection: number): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | Number returned after **connectServiceExtensionAbility** is called. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void
```

Starts an ability with a specified account. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void--><!--Device-InputMethodExtensionContext-startAbilityWithAccount(want: Want, accountId: number, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability. |
| accountId | number | Yes | ID of the target system account. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the starting is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-caller-released) | The caller has been released. |

## startAbilityWithAccount

```TypeScript
startAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

Starts an ability with a specified account. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-startAbilityWithAccount(want: Want, accountId: number): Promise<void>--><!--Device-InputMethodExtensionContext-startAbilityWithAccount(want: Want, accountId: number): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability. |
| accountId | number | Yes | ID of the target system account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000001](../../apis-ability-kit/errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../../apis-ability-kit/errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../../apis-ability-kit/errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../../apis-ability-kit/errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../../apis-ability-kit/errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../../apis-ability-kit/errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../../apis-ability-kit/errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../../apis-ability-kit/errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../../apis-ability-kit/errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../../apis-ability-kit/errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../../apis-ability-kit/errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../../apis-ability-kit/errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed. 2. System service failed to communicate with dependency module. |
| [16000053](../../apis-ability-kit/errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../../apis-ability-kit/errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../../apis-ability-kit/errorcode-ability.md#16200001-caller-released) | The caller has been released. |

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

Destroys this input method extension. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [destroy](arkts-ime-inputmethodextensioncontext-c.md#destroy-1)(callback: AsyncCallback&lt;void&gt;)

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-terminateSelf(callback: AsyncCallback<void>): void--><!--Device-InputMethodExtensionContext-terminateSelf(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

Destroys this input method extension. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [destroy](arkts-ime-inputmethodextensioncontext-c.md#destroy)()

**Model restriction:** This API can be used only in the stage model.

<!--Device-InputMethodExtensionContext-terminateSelf(): Promise<void>--><!--Device-InputMethodExtensionContext-terminateSelf(): Promise<void>-End-->

**System capability:** SystemCapability.MiscServices.InputMethodFramework

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
