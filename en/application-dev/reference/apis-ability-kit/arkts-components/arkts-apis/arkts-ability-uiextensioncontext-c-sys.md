# UIExtensionContext

UIExtensionContext provides the context environment for [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md). It inherits from [ExtensionContext](arkts-ability-extensioncontext-c.md) and provides UIExtensionAbility-related configuration and APIs for operating the UIExtensionAbility. For example, you can use the APIs to start a UIExtensionAbility.

**Inheritance/Implementation:** UIExtensionContext extends [ExtensionContext](arkts-ability-extensioncontext-c.md)

**Since:** 10

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## connectServiceExtensionAbilityWithRootHostToken

```TypeScript
connectServiceExtensionAbilityWithRootHostToken(want: Want, connect: ConnectOptions): number
```

Connects the current UI extension to an service extension ability with a root host token. If the target service extension ability is visible, you can connect the target service extension ability; If the target service extension ability is invisible, you need to apply for permission:ohos.permission.START_INVISIBLE_ABILITY to connect target invisible service extension ability. If the target service extension ability is in cross-device, you need to apply for permission:ohos.permission.DISTRIBUTED_DATASYNC.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | The element name of the service ability |
| connect | [ConnectOptions](arkts-ability-connectoptions-connectoptions-i.md) | Yes | The remote object instance |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the number code of the ability connected |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. Possible cause: target service extension ability is in cross-device and needed designated permission to be started, but call ability do not have this permission. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000002](../errorcode-ability.md#16000002-incorrect-ability-type) | Incorrect ability type. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000012](../errorcode-ability.md#16000012-application-under-control) | The application is controlled. |
| [16000013](../errorcode-ability.md#16000013-application-controlled-by-edm) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
| [16000053](../errorcode-ability.md#16000053-ability-not-in-the-foreground) | The ability is not on the top of the UI. |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service. |

## setHostPageOverlayForbidden

```TypeScript
setHostPageOverlayForbidden(isForbidden: boolean) : void
```

Sets whether the page started by the [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) can be overlaid by the page of the user.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> This API must be called before a window is created. You are advised to call it within the
> [onCreate](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#oncreate) lifecycle of the
> [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isForbidden | boolean | Yes | Whether the page started by the [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md) can be overlaid by the page of the user. **true** if the page can be overlaid, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

## startAbilityForResultAsCaller

```TypeScript
startAbilityForResultAsCaller(want: Want, options?: StartOptions): Promise<AbilityResult>
```

Starts an ability with the caller information specified. The caller information is carried in **want** and identified at the system service layer. The ability can obtain the caller information from the **want** parameter in the **onCreate** lifecycle callback. When this API is used to start an ability, the caller information carried in **want** is not overwritten by the current application information. The system service layer can obtain the initial caller information. This API uses a promise to return the result.

- Normally, you can call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the ability. The result is returned to the caller.  
- If an exception occurs, for example, the ability is killed, an error message, in which **resultCode** is **-1**,  
is returned to the caller.  
- If different applications call this API to start an ability that uses the singleton mode and then call [terminateSelfWithResult](arkts-ability-uiabilitycontext-c.md#terminateselfwithresult) to terminate the ability, the normal result is returned to the last caller, and an exception message, in which **resultCode** is **-1**, is returned to others.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information about the target ability. |
| options | [StartOptions](arkts-ability-app-ability-startoptions-startoptions-c.md) | No | Parameters used for starting the ability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityResult](arkts-ability-abilityresult-abilityresult-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16000069](../errorcode-ability.md#16000069-extensionability-fails-to-start-a-third-party-application-in-strict-mode) | The extension cannot start the third party application. |
| [16000070](../errorcode-ability.md#16000070-extensionability-fails-to-start-a-serviceextensionability-in-strict-mode) | The extension cannot start the service. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |
| [16000071](../errorcode-ability.md#16000071-application-clone-is-not-supported) | App clone is not supported.<br>**Applicable version:** 14 and later |
| [16000072](../errorcode-ability.md#16000072-multi-app-mode-is-not-supported) | App clone or multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid.<br>**Applicable version:** 14 and later |
| [16000077](../errorcode-ability.md#16000077-number-of-application-instances-reaches-the-upper-limit) | The number of app instances reaches the limit.<br>**Applicable version:** 14 and later |
| [16000078](../errorcode-ability.md#16000078-multi-instance-mode-is-not-supported) | The multi-instance is not supported.<br>**Applicable version:** 14 and later |
| [16000079](../errorcode-ability.md#16000079-app_instance_key-cannot-be-specified) | The APP_INSTANCE_KEY cannot be specified.<br>**Applicable version:** 14 and later |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported.<br>**Applicable version:** 14 and later |

## startServiceExtensionAbility

```TypeScript
startServiceExtensionAbility(want: Want): Promise<void>
```

Starts a ServiceExtensionAbility. This API uses a promise to return the result.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the ServiceExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
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
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

## startServiceExtensionAbilityWithAccount

```TypeScript
startServiceExtensionAbilityWithAccount(want: Want, accountId: number): Promise<void>
```

Starts a ServiceExtensionAbility under a specified system account. This API uses a promise to return the result.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).
> 
> Permission verification is not required when **accountId** specifies the current user.

**Since:** 18

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information for starting the ServiceExtensionAbility. |
| accountId | number | Yes | ID of a system account. For details, see [getCreatedOsAccountsCount](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountcount). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
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
| [16000019](../errorcode-ability.md#16000019-no-matching-ability-found-for-implicit-start) | No matching ability is found. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |

## startUIAbilities

```TypeScript
startUIAbilities(wantList: Array<Want>): Promise<void>
```

Starts multiple UIAbility components simultaneously. This API uses a promise to return the result. You can pass the Want information of multiple UIAbility instances, which can point to one or more applications. If all the UIAbility instances can be started successfully, the system displays these UIAbility instances in multiple windows simultaneously. Depending on the window handling, different devices may have varying display effects (including window shape, quantity, and layout). This API can be properly called only on phones and tablets. If it is called on other device types, error code 801 is returned.

> **NOTE:** 
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wantList | Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Yes | List of launch parameters for multiple UIAbility components to be started simultaneously. A maximum of four Want objects can be passed. The **Want** parameter does not support implicit launch, cross-user launch, distributed launch, instant installation, or on-demand loading. By default, the main application is launched unless specified otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | The specified ability does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |
| [16200001](../errorcode-ability.md#16200001-caller-released) | The caller has been released. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid. |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported. |
| [16000120](../errorcode-ability.md#16000120-number-of-elements-in-wantlist-exceeds-4-or-is-less-than-1) | A maximum of four UIAbility instances can be started simultaneously. The current parameter exceeds the maximum number or is less than 1. |
| [16000121](../errorcode-ability.md#16000121-target-component-is-not-a-uiability) | The target component type is not a UIAbility. |
| [16000122](../errorcode-ability.md#16000122-target-component-is-intercepted-by-the-system-control-module) | The target component is blocked by the system module and does not support startup. |
| [16000123](../errorcode-ability.md#16000123-implicit-startup-is-not-supported) | Implicit startup is not supported. |
| [16000124](../errorcode-ability.md#16000124-starting-a-distributed-uiability-is-not-supported) | Starting a remote UIAbility is not supported. |
| [16000125](../errorcode-ability.md#16000125-starting-a-plugin-uiability-is-not-supported) | Starting a plugin UIAbility is not supported. |
| [16000126](../errorcode-ability.md#16000126-dlp-files-cannot-be-started) | Starting DLP files is not supported. |

## startUIAbilitiesInSplitWindowMode

```TypeScript
startUIAbilitiesInSplitWindowMode(primaryWindowId: number, secondaryWant: Want): Promise<void>
```

Starts a second UIAbility after the first UIAbility instance is created, and displays them in split-screen mode. This API uses a promise to return the result. This API can be properly called only on phones. If it is called on other device types, error code 801 is returned.

> **NOTE:** 
> 
> If the first UIAbility instance is destroyed, the second UIAbility is started in full-screen mode.
> 
> The second UIAbility supports only
> [explicit startup](../../../application-models/explicit-implicit-want-mappings.md#matching-rules-of-explicit-want)
> .
> 
> If the caller is running in the background, the ohos.permission.START_ABILITIES_FROM_BACKGROUND permission is
> required (available only for system applications).
> 
> For details about the startup rules for the components in the stage model, see
> [Component Startup Rules (Stage Model)](../../../application-models/component-startup-rules.md).

**Since:** 21

**Required permissions:** ohos.permission.START_ABILITIES_FROM_BACKGROUND

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| primaryWindowId | number | Yes | ID of the main window of the first UIAbility. The window ID is a property defined in [WindowProperties](../../../reference/apis-arkui/arkts-apis-window-i.md#windowproperties), which can be obtained by calling [getWindowProperties()](../../../reference/apis-arkui/arkts-apis-window-Window.md#getwindowproperties9). |
| secondaryWant | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want information required for starting the second UIAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [16000001](../errorcode-ability.md#16000001-ability-name-does-not-exist) | Target UIAbility does not exist. |
| [16000004](../errorcode-ability.md#16000004-visibility-verification-failure) | Cannot start an invisible component. |
| [16000005](../errorcode-ability.md#16000005-process-permission-verification-failure) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-cross-user-operation-is-not-allowed) | Cross-user operations are not allowed. |
| [16000008](../errorcode-ability.md#16000008-crowdtesting-application-expires) | The crowdtesting application expires. |
| [16000009](../errorcode-ability.md#16000009-ability-start-or-stop-failure-in-wukong-mode) | An ability cannot be started or stopped in Wukong mode. |
| [16000011](../errorcode-ability.md#16000011-context-does-not-exist) | The context does not exist. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Failed to connect to the system service or system server handle failed. |
| [16000073](../errorcode-ability.md#16000073-appcloneindex-is-invalid) | The app clone index is invalid. |
| [16000076](../errorcode-ability.md#16000076-app_instance_key-does-not-exist) | The app instance key is invalid. |
| [16000080](../errorcode-ability.md#16000080-new-instances-cannot-be-created) | Creating a new instance is not supported. |
| [16000122](../errorcode-ability.md#16000122-target-component-is-intercepted-by-the-system-control-module) | The target component is blocked by the system module and does not support startup. |
| [16000123](../errorcode-ability.md#16000123-implicit-startup-is-not-supported) | Implicit startup is not supported. |
| [16000124](../errorcode-ability.md#16000124-starting-a-distributed-uiability-is-not-supported) | Starting a remote UIAbility is not supported. |
| [16000125](../errorcode-ability.md#16000125-starting-a-plugin-uiability-is-not-supported) | Starting a plugin UIAbility is not supported. |
| [16000126](../errorcode-ability.md#16000126-dlp-files-cannot-be-started) | Starting DLP files is not supported. |
