# UIExtensionContext

UIExtensionContext provides the context environment for [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md). It inherits from [ExtensionContext](arkts-ability-extensioncontext-c.md) and provides UIExtensionAbility-related configuration and APIs for operating the UIExtensionAbility. For example, you can use the APIs to start a UIExtensionAbility.

**Inheritance/Implementation:** UIExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbility

```TypeScript
connectServiceExtensionAbility(want: Want, options: ConnectOptions): number
```

Connects this UIExtensionAbility to a ServiceExtensionAbility. It enables communication with the ServiceExtensionAbility via a proxy, allowing access to the capabilities exposed by the ServiceExtensionAbility. ServiceExtensionAbility is a special type of [ExtensionAbility](../../../application-models/extensionability-overview.md) provided by the system. It is designed to offer background services for specific scenarios and is not customizable by developers. It can be connected to by other components and handles requests in the background based on the caller information.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information required for connecting to the ServiceExtensionAbility, including the ability name and bundle name. |
| options | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | Yes | Callback used to return the information indicating that the connection is successful, failed, or interrupted. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Connection ID. The client can call [disconnectServiceExtensionAbility](#disconnectserviceextensionability) with this ID for disconnection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service. |

## connectUIServiceExtensionAbility

```TypeScript
connectUIServiceExtensionAbility(want: Want, callback: UIServiceExtensionConnectCallback) : Promise<UIServiceProxy>
```

Connects to a UIServiceExtensionAbility. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information used for connection. |
| callback | [UIServiceExtensionConnectCallback](arkts-ability-uiserviceextensionconnectcallback-i.md) | Yes | Callback for connecting to the UIServiceExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[UIServiceProxy](arkts-ability-uiserviceproxy-i.md)&gt; | Promise used to return a [UIServiceProxy](arkts-ability-uiserviceproxy-i.md) object when the UIServiceExtensionAbility is connected. This object can be used to send data to the UIServiceExtensionAbility. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number, callback: AsyncCallback<void>): void
```

Disconnects from a ServiceExtensionAbility. Once the connection is terminated, set the remote object, which is returned when the connection is established, to null. This API uses an asynchronous callback to return the result. ServiceExtensionAbility is a special type of [ExtensionAbility](../../../application-models/extensionability-overview.md) provided by the system. It is designed to offer background services for specific scenarios and is not customizable by developers. It can be connected to by other components and handles requests in the background based on the caller information.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | ID of the connected ServiceExtensionAbility, that is, **connectionId** returned by **connectServiceExtensionAbility**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the disconnection is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

## disconnectServiceExtensionAbility

```TypeScript
disconnectServiceExtensionAbility(connection: number): Promise<void>
```

Disconnects from a ServiceExtensionAbility. Once the connection is terminated, set the remote object, which is returned when the connection is established, to null. This API uses a promise to return the result. ServiceExtensionAbility is a special type of [ExtensionAbility](../../../application-models/extensionability-overview.md) provided by the system. It is designed to offer background services for specific scenarios and is not customizable by developers. It can be connected to by other components and handles requests in the background based on the caller information.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| connection | number | Yes | ID of the connected ServiceExtensionAbility, that is, **connectionId** returned by [connectServiceExtensionAbility](#connectserviceextensionability). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

## disconnectUIServiceExtensionAbility

```TypeScript
disconnectUIServiceExtensionAbility(proxy: UIServiceProxy): Promise<void>
```

Disconnects from a UIServiceExtensionAbility. This API uses a promise to return the result.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| proxy | [UIServiceProxy](arkts-ability-uiserviceproxy-i.md) | Yes | Proxy used returned by calling [connectUIServiceExtensionAbility](#connectuiserviceextensionability). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

## openAtomicService

```TypeScript
openAtomicService(appId: string, options?: AtomicServiceOptions): Promise<AbilityResult>
```

Opens an atomic service in an independent window and returns the result. This API uses a promise to return the result. The following situations may be possible for a started atomic service:

- Normally, you can call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the atomic service. The result is returned to the caller.  
- If an exception occurs, for example, the atomic service is killed, an error message, in which **resultCode** is  
**-1**, is returned to the caller.  
- If different applications call this API to start an atomic service and then call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the atomic service, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Unique ID of the application, which is allocated by the cloud. |
| options | [AtomicServiceOptions](arkts-ability-app-ability-atomicserviceoptions-atomicserviceoptions-c.md) | No | Parameter carried in the request for starting the atomic service. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise used to return the information to the caller. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000003](../errorcode-ability.md#16000003-id-does-not-exist) | The specified ID does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

## openLink

```TypeScript
openLink(link: string, options?: OpenLinkOptions, callback?: AsyncCallback<AbilityResult>): Promise<void>
```

Starts a UIAbility by using App Linking or Deep Linking. This API uses a promise to return the result. A URL in the standard format is passed in to the **link** field to start the target UIAbility based on the implicit Want matching rules. The target UIAbility must have the following filter characteristics to process links of App Linking:

- The **actions** field must contain **ohos.want.action.viewData**.  
- The **entities** field must contain **entity.system.browsable**.  
- The **uris** field must contain elements whose **scheme** is **https** and **domainVerify** is **true**.  
If you want to obtain the result after the started UIAbility is terminated, set the **callback** parameter. For details about how to use this parameter, see [startAbilityForResult](#startabilityforresult). If an input parameter is invalid, for example, a mandatory parameter is not set or the URL set in **link** is not in the standard format, an exception is thrown. If the parameter verification is successful but an error occurs when starting the target UIAbility, the error information is returned through promise.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| link | string | Yes | URL to open, which must be in the standard format. |
| options | [OpenLinkOptions](arkts-ability-app-ability-openlinkoptions-openlinkoptions-i.md) | No | Options of the URL. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | No | Callback used to return the result. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000136](../errorcode-ability.md#16000136-prohibited-from-launching-the-applications-own-uiability-via-app-linking) | The UIAbility is prohibited from launching itself via App Linking.<br>**Applicable version:** 23 and later |

## reportDrawnCompleted

```TypeScript
reportDrawnCompleted(callback: AsyncCallback<void>): void
```

Called when the window content associated with the UIExtensionAbility finishes drawing. The system uses the information to optimize resource allocation, thereby enhancing the efficiency of application startup and display. This API uses an asynchronous callback to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the event is reported, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

## setColorMode

```TypeScript
setColorMode(colorMode: ConfigurationConstant.ColorMode): void
```

Sets the dark/light color mode for this UIExtensionAbility. Before calling this API, ensure that the page corresponding to the UIExtensionContext has been loaded. This API can be called only by the main thread.

> **NOTE:** 
> 
> - After this API is called, a new resource manager object is created. If a resource manager was previously cached , it should be updated accordingly.
> 
> - The priority of the dark/light color mode is as follows: UIExtensionAbility dark/light color mode Application dark/light color mode (set via [ApplicationContext.setColorMode](arkts-ability-applicationcontext-c.md#setcolormode))System dark/light color mode.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorMode | [ConfigurationConstant.ColorMode](arkts-ability-configurationconstant-colormode-e.md) | Yes | Color mode. The options are as follows:<br> - **COLOR_MODE_DARK**: dark mode.<br> - **COLOR_MODE_LIGHT**: light mode.<br> - **COLOR_MODE_NOT_SET**: not set (following the system or application). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |

## startAbility

```TypeScript
startAbility(want: Want, callback: AsyncCallback<void>): void
```

Starts a UIAbility. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want required for starting the UIAbility, which contains information such as the name of the UIAbility to start. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the UIAbility is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000018](../errorcode-ability.md#16000018-restricting-redirection-to-third-party-applications-of-api-version-11-or-later) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**Applicable version:** 12 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application.<br>**Applicable version:** 12 and later |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startAbility

```TypeScript
startAbility(want: Want, options: StartOptions, callback: AsyncCallback<void>): void
```

Starts a UIAbility. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want required for starting the UIAbility, which contains information such as the name of the UIAbility to start. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Extra parameters used for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the UIAbility is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000018](../errorcode-ability.md#16000018-restricting-redirection-to-third-party-applications-of-api-version-11-or-later) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**Applicable version:** 12 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application.<br>**Applicable version:** 12 and later |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startAbility

```TypeScript
startAbility(want: Want, options?: StartOptions): Promise<void>
```

Starts a UIAbility. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want required for starting the UIAbility, which contains information such as the name of the UIAbility to start. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Extra parameters used for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000018](../errorcode-ability.md#16000018-restricting-redirection-to-third-party-applications-of-api-version-11-or-later) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**Applicable version:** 12 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application.<br>**Applicable version:** 12 and later |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, callback: AsyncCallback<AbilityResult>): void
```

Starts a UIAbility and returns the exit result of the launched UIAbility via a callback. This API uses an asynchronous callback to return the result. The following situations may be possible for a started UIAbility:

- Normally, you can call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the UIAbility. The result is returned to the caller.  
- If an exception occurs, for example, the UIAbility is killed, an error message, in which **resultCode** is **-1**  
, is returned to the initiator UIAbility.  
- If different applications call this API to start a UIAbility that uses the singleton mode and then call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the UIAbility, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want required for starting the UIAbility, which contains information such as the name of the UIAbility to start. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000018](../errorcode-ability.md#16000018-restricting-redirection-to-third-party-applications-of-api-version-11-or-later) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**Applicable version:** 12 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application.<br>**Applicable version:** 12 and later |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options: StartOptions, callback: AsyncCallback<AbilityResult>): void
```

Starts a UIAbility and returns the exit result of the launched UIAbility via a callback. This API uses an asynchronous callback to return the result. The following situations may be possible for a started UIAbility:

- Normally, you can call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the UIAbility. The result is returned to the caller.  
- If an exception occurs, for example, the UIAbility is killed, an error message, in which **resultCode** is **-1**  
, is returned to the initiator UIAbility.  
- If different applications call this API to start a UIAbility that uses the singleton mode and then call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the UIAbility, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want required for starting the UIAbility, which contains information such as the name of the UIAbility to start. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | Yes | Extra parameters used for starting the UIAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000018](../errorcode-ability.md#16000018-restricting-redirection-to-third-party-applications-of-api-version-11-or-later) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**Applicable version:** 12 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application.<br>**Applicable version:** 12 and later |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startAbilityForResult

```TypeScript
startAbilityForResult(want: Want, options?: StartOptions): Promise<AbilityResult>
```

Starts a UIAbility and returns the exit result of the launched UIAbility via a callback. This API uses a promise to return the result. The following situations may be possible for a started UIAbility:

- Normally, you can call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the UIAbility. The result is returned to the caller.  
- If an exception occurs, for example, the UIAbility is killed, an error message, in which **resultCode** is **-1**  
, is returned to the initiator UIAbility.  
- If different applications call this API to start a UIAbility that uses the singleton mode and then call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the UIAbility, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want required for starting the UIAbility, which contains information such as the name of the UIAbility to start. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Extra parameters used for starting the UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise used to return the exit result of the launched UIAbility. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000010](../errorcode-ability.md#16000010-continuation-flag-is-forbidden) | The call with the continuation and prepare continuation flag is forbidden. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000055](../errorcode-ability.md#16000055-installation-free-timeout) | Installation-free timed out. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000018](../errorcode-ability.md#16000018-restricting-redirection-to-third-party-applications-of-api-version-11-or-later) | Redirection to a third-party application is not allowed in API version greater than 11.<br>**Applicable version:** 12 and later |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found.<br>**Applicable version:** 12 and later |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application.<br>**Applicable version:** 12 and later |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service.<br>**Applicable version:** 12 and later |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid.<br>**Applicable version:** 12 and later |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startUIServiceExtensionAbility

```TypeScript
startUIServiceExtensionAbility(want: Want): Promise<void>
```

Starts a UIServiceExtensionAbility. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want for starting the UIServiceExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

## terminateSelf

```TypeScript
terminateSelf(callback: AsyncCallback<void>): void
```

Destroys this UIExtensionAbility and closes the corresponding window. This API uses an asynchronous callback to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## terminateSelf

```TypeScript
terminateSelf(): Promise<void>
```

Destroys this UIExtensionAbility and closes the corresponding window. This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult, callback: AsyncCallback<void>): void
```

Destroys this UIExtensionAbility, closes the corresponding window, and returns the result to the caller of the UIExtensionAbility (usually a system service). This API uses an asynchronous callback to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | Yes | Information returned to the caller of the UIExtensionAbility. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## terminateSelfWithResult

```TypeScript
terminateSelfWithResult(parameter: AbilityResult): Promise<void>
```

Destroys this UIExtensionAbility, closes the corresponding window, and returns the result to the caller of the UIExtensionAbility (usually a system service). This API uses a promise to return the result.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [AbilityResult](arkts-ability-abilityresult-abilityresult-i.md) | Yes | Information returned to the caller of the UIExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
