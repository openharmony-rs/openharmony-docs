# Context

The context of an ability or an application. It allows access to application-specific resources, request and verification permissions. Can only be obtained through the ability.

**Inheritance/Implementation:** Context extends [BaseContext](arkts-ability-basecontext-c.md)

**Since:** 6

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## getAbilityInfo

```TypeScript
getAbilityInfo(callback: AsyncCallback<AbilityInfo>): void
```

Checks the detailed information of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt; | Yes | Return the detailed information of the current belonging Ability. |

## getAbilityInfo

```TypeScript
getAbilityInfo(): Promise<AbilityInfo>
```

Checks the detailed information of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt; | Return the detailed information of the current belonging Ability. |

## getApplicationContext

```TypeScript
getApplicationContext(): Context
```

Obtains the context of this application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Context](arkts-ability-context-context-depr-i.md) | Return application context information. |

## getApplicationInfo

```TypeScript
getApplicationInfo(callback: AsyncCallback<ApplicationInfo>): void
```

Obtains information about the current application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)&gt; | Yes | Returns information about the current application. |

## getApplicationInfo

```TypeScript
getApplicationInfo(): Promise<ApplicationInfo>
```

Obtains information about the current application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)&gt; | Information about the current application. |

## getAppType

```TypeScript
getAppType(callback: AsyncCallback<string>): void
```

Obtains the application type.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the type of the current application. |

## getAppType

```TypeScript
getAppType(): Promise<string>
```

Obtains the application type.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the type of this app. |

## getAppVersionInfo

```TypeScript
getAppVersionInfo(callback: AsyncCallback<AppVersionInfo>): void
```

Obtains the application version information.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AppVersionInfo](arkts-ability-appversioninfo-appversioninfo-depr-i.md)&gt; | Yes | Return application version information. |

## getAppVersionInfo

```TypeScript
getAppVersionInfo(): Promise<AppVersionInfo>
```

Obtains the application version information.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AppVersionInfo](arkts-ability-appversioninfo-appversioninfo-depr-i.md)&gt; | Return application version information. |

## getBundleName

```TypeScript
getBundleName(callback: AsyncCallback<string>): void
```

Obtains the bundle name of the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the Bundle name of the current capability. |

## getBundleName

```TypeScript
getBundleName(): Promise<string>
```

Obtains the bundle name of the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | The Bundle name of the current capability. |

## getCacheDir

```TypeScript
getCacheDir(callback: AsyncCallback<string>): void
```

Obtains the cache directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the internal storage directory of the application. |

## getCacheDir

```TypeScript
getCacheDir(): Promise<string>
```

Obtains the cache directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the internal storage directory of the application. |

## getCallingBundle

```TypeScript
getCallingBundle(callback: AsyncCallback<string>): void
```

Obtains the bundle name of the ability that called the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the Bundle name of the ability caller. |

## getCallingBundle

```TypeScript
getCallingBundle(): Promise<string>
```

Obtains the bundle name of the ability that called the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the Bundle name of the ability caller. |

## getDisplayOrientation

```TypeScript
getDisplayOrientation(callback: AsyncCallback<bundle.DisplayOrientation>): void
```

Obtains the current display orientation of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md)&gt; | Yes | Indicates the realistic direction of the screen. |

## getDisplayOrientation

```TypeScript
getDisplayOrientation(): Promise<bundle.DisplayOrientation>
```

Obtains the current display orientation of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md)&gt; | Indicates the screen display direction. |

## getElementName

```TypeScript
getElementName(callback: AsyncCallback<ElementName>): void
```

Obtains the ohos.bundle.ElementName object of the current ability.This method is available only to Page abilities.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ElementName](arkts-ability-elementname-elementname-depr-i.md)&gt; | Yes | Returns the ohos.bundle.ElementName of the current capability. |

## getElementName

```TypeScript
getElementName(): Promise<ElementName>
```

Obtains the ohos.bundle.ElementName object of the current ability.This method is available only to Page abilities.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ElementName](arkts-ability-elementname-elementname-depr-i.md)&gt; | The ohos.bundle.ElementName object of the current capability. |

## getExternalCacheDir

```TypeScript
getExternalCacheDir(callback: AsyncCallback<string>): void
```

Obtains the absolute path to the application-specific cache directory

**Since:** 6

**Deprecated since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the absolute path of the application's cache directory. |

## getExternalCacheDir

```TypeScript
getExternalCacheDir(): Promise<string>
```

Obtains the absolute path to the application-specific cache directory

**Since:** 6

**Deprecated since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Return the cache directory of the application. |

## getFilesDir

```TypeScript
getFilesDir(callback: AsyncCallback<string>): void
```

Obtains the file directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Return the file directory of this application on internal storage. |

## getFilesDir

```TypeScript
getFilesDir(): Promise<string>
```

Obtains the file directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Return the file directory of this application on internal storage. |

## getHapModuleInfo

```TypeScript
getHapModuleInfo(callback: AsyncCallback<HapModuleInfo>): void
```

Obtains the ModuleInfo object for this application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HapModuleInfo](arkts-ability-hapmoduleinfo-hapmoduleinfo-depr-i.md)&gt; | Yes | Returns the ModuleInfo object of the application. |

## getHapModuleInfo

```TypeScript
getHapModuleInfo(): Promise<HapModuleInfo>
```

Obtains the ModuleInfo object for this application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HapModuleInfo](arkts-ability-hapmoduleinfo-hapmoduleinfo-depr-i.md)&gt; | Return to the ModuleInfo of the application and enjoy it. |

## getOrCreateDistributedDir

```TypeScript
getOrCreateDistributedDir(): Promise<string>
```

Obtains the distributed file path for storing ability or application data files. If the distributed file path does not exist, the system will create a path and return the created path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the distributed file path of the Ability or application. If it is the first call, a directory will be created. |

## getOrCreateDistributedDir

```TypeScript
getOrCreateDistributedDir(callback: AsyncCallback<string>): void
```

Obtains the distributed file path for storing ability or application data files. If the distributed file path does not exist, the system will create a path and return the created path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the distributed file path of Ability or application. If the path does not exist,the system will create a path and return the created path. |

## getOrCreateLocalDir

```TypeScript
getOrCreateLocalDir(): Promise<string>
```

Get the local root dir of an app. If it is the first call, the dir will be created. If in the context of the ability, return the root dir of the ability; if in the context of the application, return the root dir of the application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | the root dir |

## getOrCreateLocalDir

```TypeScript
getOrCreateLocalDir(callback: AsyncCallback<string>): void
```

Get the local root dir of an app. If it is the first call, the dir will be created. If in the context of the ability, return the root dir of the ability; if in the context of the application, return the root dir of the application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the local root directory of the application. |

## getProcessInfo

```TypeScript
getProcessInfo(callback: AsyncCallback<ProcessInfo>): void
```

Obtains information about the current process, including the process ID and name.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ProcessInfo](arkts-ability-processinfo-processinfo-depr-i.md)&gt; | Yes | Return current process information. |

## getProcessInfo

```TypeScript
getProcessInfo(): Promise<ProcessInfo>
```

Obtains information about the current process, including the process ID and name.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ProcessInfo](arkts-ability-processinfo-processinfo-depr-i.md)&gt; | Information about the current process. |

## getProcessName

```TypeScript
getProcessName(callback: AsyncCallback<string>): void
```

Obtains the name of the current process.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Return current process name. |

## getProcessName

```TypeScript
getProcessName(): Promise<string>
```

Obtains the name of the current process.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the name of the current process. |

## isUpdatingConfigurations

```TypeScript
isUpdatingConfigurations(callback: AsyncCallback<boolean>): void
```

Checks whether the configuration of this ability is changing.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | True if the configuration of the capability is being changed, otherwise false. |

## isUpdatingConfigurations

```TypeScript
isUpdatingConfigurations(): Promise<boolean>
```

Checks whether the configuration of this ability is changing.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | true if the configuration of this ability is changing and false otherwise. |

## printDrawnCompleted

```TypeScript
printDrawnCompleted(callback: AsyncCallback<void>): void
```

Inform the system of the time required for drawing this Page ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Represents the specified callback method. |

## printDrawnCompleted

```TypeScript
printDrawnCompleted(): Promise<void>
```

Inform the system of the time required for drawing this Page ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise form returns the result. |

## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(
    permissions: Array<string>,
    requestCode: number,
    resultCallback: AsyncCallback<PermissionRequestResult>
  ): void
```

Requests certain permissions from the system.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permissions | Array&lt;string&gt; | Yes | Indicates the list of permissions to be requested.parameter cannot be null. |
| requestCode | number | Yes | Indicates the request code to be passed to the PermissionRequestResult |
| resultCallback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PermissionRequestResult](arkts-ability-context-permissionrequestresult-depr-i.md)&gt; | Yes | Return authorization result information. |

## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(permissions: Array<string>, requestCode: number): Promise<PermissionRequestResult>
```

Requests certain permissions from the system.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permissions | Array&lt;string&gt; | Yes | Indicates the list of permissions to be requested.Parameter cannot be null. |
| requestCode | number | Yes | Indicates the request code to be passed to the PermissionRequestResult |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PermissionRequestResult](arkts-ability-context-permissionrequestresult-depr-i.md)&gt; | Indicates the request code to be passed to PermissionRequestResult. |

## setDisplayOrientation

```TypeScript
setDisplayOrientation(orientation: bundle.DisplayOrientation, callback: AsyncCallback<void>): void
```

Sets the display orientation of the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md) | Yes | Indicates the new orientation for the current ability. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the realistic direction of the screen. |

## setDisplayOrientation

```TypeScript
setDisplayOrientation(orientation: bundle.DisplayOrientation): Promise<void>
```

Sets the display orientation of the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md) | Yes | Indicates the new orientation for the current ability. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(show: boolean, callback: AsyncCallback<void>): void
```

Sets whether to show this ability on top of the lock screen whenever the lock screen is displayed, keeping the ability in the ACTIVE state. The interface can only take effect in API8 and below versions.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes | Specifies whether to show this ability on top of the lock screen. The value true means to show it on the lock screen, and the value false means not. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Returns the callback result. |

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(show: boolean): Promise<void>
```

Sets whether to show this ability on top of the lock screen whenever the lock screen is displayed, keeping the ability in the ACTIVE state. The interface can only take effect in API8 and below versions.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes | Specifies whether to show this ability on top of the lock screen. The value true means to show it on the lock screen, and the value false means not. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean, callback: AsyncCallback<void>): void
```

Sets whether to wake up the screen when this ability is restored.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** setWakeUpScreen

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wakeUp | boolean | Yes | Specifies whether to wake up the screen. The value true means to wake it up, and the value false means not. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Returns the callback result. |

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean): Promise<void>
```

Sets whether to wake up the screen when this ability is restored.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** setWakeUpScreen

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wakeUp | boolean | Yes | Specifies whether to wake up the screen. The value true means to wake it up, and the value false means not. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

## verifyPermission

```TypeScript
verifyPermission(permission: string, options?: PermissionOptions): Promise<number>
```

Verify whether the specified permission is allowed for a particular pid and uid running in the system. Pid and uid are optional. If you do not pass in pid and uid, it will check your own permission.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permission | string | Yes | The name of the specified permission. |
| options | [PermissionOptions](arkts-ability-context-permissionoptions-depr-i.md) | No | Permission Options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | asynchronous callback with `0` if the PID and UID have the permission; callback with `-1` otherwise. |

## verifyPermission

```TypeScript
verifyPermission(permission: string, options: PermissionOptions, callback: AsyncCallback<number>): void
```

Verify whether the specified permission is allowed for a particular pid and uid running in the system. Pid and uid are optional. If you do not pass in pid and uid, it will check your own permission.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permission | string | Yes | The name of the specified permission |
| options | [PermissionOptions](arkts-ability-context-permissionoptions-depr-i.md) | Yes | Permission Options |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Return permission verification result, 0 has permission, -1 has no permission. |

## verifyPermission

```TypeScript
verifyPermission(permission: string, callback: AsyncCallback<number>): void
```

Verify whether the specified permission is allowed for a particular pid and uid running in the system. Pid and uid are optional. If you do not pass in pid and uid, it will check your own permission.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permission | string | Yes | The name of the specified permission |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Return permission verification result, 0 has permission, -1 has no permission. |
