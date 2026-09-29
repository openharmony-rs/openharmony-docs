# Context

```TypeScript
export interface Context extends BaseContext
```

The context of an ability or an application. It allows access to application-specific resources, request and verification permissions. Can only be obtained through the ability.

**Inheritance/Implementation:** Context extends [BaseContext](arkts-ability-basecontext-c.md)

**Since:** 6

<!--Device-unnamed-export interface Context extends BaseContext--><!--Device-unnamed-export interface Context extends BaseContext-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## getAbilityInfo

```TypeScript
getAbilityInfo(callback: AsyncCallback<AbilityInfo>): void
```

Checks the detailed information of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getAbilityInfo(callback: AsyncCallback<AbilityInfo>): void--><!--Device-Context-getAbilityInfo(callback: AsyncCallback<AbilityInfo>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt; | Yes | Return the detailed information of the current belonging Ability. |

<a id="getabilityinfo-1"></a>

## getAbilityInfo

```TypeScript
getAbilityInfo(): Promise<AbilityInfo>
```

Checks the detailed information of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getAbilityInfo(): Promise<AbilityInfo>--><!--Device-Context-getAbilityInfo(): Promise<AbilityInfo>-End-->

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

<!--Device-Context-getApplicationContext(): Context--><!--Device-Context-getApplicationContext(): Context-End-->

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

<!--Device-Context-getApplicationInfo(callback: AsyncCallback<ApplicationInfo>): void--><!--Device-Context-getApplicationInfo(callback: AsyncCallback<ApplicationInfo>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApplicationInfo](arkts-ability-applicationinfo-applicationinfo-depr-i.md)&gt; | Yes | Returns information about the current application. |

<a id="getapplicationinfo-1"></a>

## getApplicationInfo

```TypeScript
getApplicationInfo(): Promise<ApplicationInfo>
```

Obtains information about the current application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getApplicationInfo(): Promise<ApplicationInfo>--><!--Device-Context-getApplicationInfo(): Promise<ApplicationInfo>-End-->

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

<!--Device-Context-getAppType(callback: AsyncCallback<string>): void--><!--Device-Context-getAppType(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the type of the current application. |

<a id="getapptype-1"></a>

## getAppType

```TypeScript
getAppType(): Promise<string>
```

Obtains the application type.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getAppType(): Promise<string>--><!--Device-Context-getAppType(): Promise<string>-End-->

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

<!--Device-Context-getAppVersionInfo(callback: AsyncCallback<AppVersionInfo>): void--><!--Device-Context-getAppVersionInfo(callback: AsyncCallback<AppVersionInfo>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AppVersionInfo](arkts-ability-appversioninfo-appversioninfo-depr-i.md)&gt; | Yes | Return application version information. |

<a id="getappversioninfo-1"></a>

## getAppVersionInfo

```TypeScript
getAppVersionInfo(): Promise<AppVersionInfo>
```

Obtains the application version information.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getAppVersionInfo(): Promise<AppVersionInfo>--><!--Device-Context-getAppVersionInfo(): Promise<AppVersionInfo>-End-->

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

<!--Device-Context-getBundleName(callback: AsyncCallback<string>): void--><!--Device-Context-getBundleName(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the Bundle name of the current capability. |

<a id="getbundlename-1"></a>

## getBundleName

```TypeScript
getBundleName(): Promise<string>
```

Obtains the bundle name of the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getBundleName(): Promise<string>--><!--Device-Context-getBundleName(): Promise<string>-End-->

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

<!--Device-Context-getCacheDir(callback: AsyncCallback<string>): void--><!--Device-Context-getCacheDir(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the internal storage directory of the application. |

<a id="getcachedir-1"></a>

## getCacheDir

```TypeScript
getCacheDir(): Promise<string>
```

Obtains the cache directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getCacheDir(): Promise<string>--><!--Device-Context-getCacheDir(): Promise<string>-End-->

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

<!--Device-Context-getCallingBundle(callback: AsyncCallback<string>): void--><!--Device-Context-getCallingBundle(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the Bundle name of the ability caller. |

<a id="getcallingbundle-1"></a>

## getCallingBundle

```TypeScript
getCallingBundle(): Promise<string>
```

Obtains the bundle name of the ability that called the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getCallingBundle(): Promise<string>--><!--Device-Context-getCallingBundle(): Promise<string>-End-->

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

<!--Device-Context-getDisplayOrientation(callback: AsyncCallback<bundle.DisplayOrientation>): void--><!--Device-Context-getDisplayOrientation(callback: AsyncCallback<bundle.DisplayOrientation>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md)&gt; | Yes | Indicates the realistic direction of the screen. |

<a id="getdisplayorientation-1"></a>

## getDisplayOrientation

```TypeScript
getDisplayOrientation(): Promise<bundle.DisplayOrientation>
```

Obtains the current display orientation of this ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getDisplayOrientation(): Promise<bundle.DisplayOrientation>--><!--Device-Context-getDisplayOrientation(): Promise<bundle.DisplayOrientation>-End-->

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

<!--Device-Context-getElementName(callback: AsyncCallback<ElementName>): void--><!--Device-Context-getElementName(callback: AsyncCallback<ElementName>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ElementName](arkts-ability-elementname-elementname-depr-i.md)&gt; | Yes | Returns the ohos.bundle.ElementName of the current capability. |

<a id="getelementname-1"></a>

## getElementName

```TypeScript
getElementName(): Promise<ElementName>
```

Obtains the ohos.bundle.ElementName object of the current ability.This method is available only to Page abilities.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getElementName(): Promise<ElementName>--><!--Device-Context-getElementName(): Promise<ElementName>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ElementName](arkts-ability-elementname-elementname-depr-i.md)&gt; | The ohos.bundle.ElementName object of the current capability. |

## getFilesDir

```TypeScript
getFilesDir(callback: AsyncCallback<string>): void
```

Obtains the file directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getFilesDir(callback: AsyncCallback<string>): void--><!--Device-Context-getFilesDir(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Return the file directory of this application on internal storage. |

<a id="getfilesdir-1"></a>

## getFilesDir

```TypeScript
getFilesDir(): Promise<string>
```

Obtains the file directory of this application on the internal storage.

**Since:** 6

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getFilesDir(): Promise<string>--><!--Device-Context-getFilesDir(): Promise<string>-End-->

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

<!--Device-Context-getHapModuleInfo(callback: AsyncCallback<HapModuleInfo>): void--><!--Device-Context-getHapModuleInfo(callback: AsyncCallback<HapModuleInfo>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[HapModuleInfo](arkts-ability-hapmoduleinfo-hapmoduleinfo-depr-i.md)&gt; | Yes | Returns the ModuleInfo object of the application. |

<a id="gethapmoduleinfo-1"></a>

## getHapModuleInfo

```TypeScript
getHapModuleInfo(): Promise<HapModuleInfo>
```

Obtains the ModuleInfo object for this application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getHapModuleInfo(): Promise<HapModuleInfo>--><!--Device-Context-getHapModuleInfo(): Promise<HapModuleInfo>-End-->

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

<!--Device-Context-getOrCreateDistributedDir(): Promise<string>--><!--Device-Context-getOrCreateDistributedDir(): Promise<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the distributed file path of the Ability or application. If it is the first call, a directory will be created. |

<a id="getorcreatedistributeddir-1"></a>

## getOrCreateDistributedDir

```TypeScript
getOrCreateDistributedDir(callback: AsyncCallback<string>): void
```

Obtains the distributed file path for storing ability or application data files. If the distributed file path does not exist, the system will create a path and return the created path.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getOrCreateDistributedDir(callback: AsyncCallback<string>): void--><!--Device-Context-getOrCreateDistributedDir(callback: AsyncCallback<string>): void-End-->

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

<!--Device-Context-getOrCreateLocalDir(): Promise<string>--><!--Device-Context-getOrCreateLocalDir(): Promise<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | the root dir |

<a id="getorcreatelocaldir-1"></a>

## getOrCreateLocalDir

```TypeScript
getOrCreateLocalDir(callback: AsyncCallback<string>): void
```

Get the local root dir of an app. If it is the first call, the dir will be created. If in the context of the ability, return the root dir of the ability; if in the context of the application, return the root dir of the application.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getOrCreateLocalDir(callback: AsyncCallback<string>): void--><!--Device-Context-getOrCreateLocalDir(callback: AsyncCallback<string>): void-End-->

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

<!--Device-Context-getProcessInfo(callback: AsyncCallback<ProcessInfo>): void--><!--Device-Context-getProcessInfo(callback: AsyncCallback<ProcessInfo>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ProcessInfo](arkts-ability-processinfo-processinfo-depr-i.md)&gt; | Yes | Return current process information. |

<a id="getprocessinfo-1"></a>

## getProcessInfo

```TypeScript
getProcessInfo(): Promise<ProcessInfo>
```

Obtains information about the current process, including the process ID and name.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getProcessInfo(): Promise<ProcessInfo>--><!--Device-Context-getProcessInfo(): Promise<ProcessInfo>-End-->

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

<!--Device-Context-getProcessName(callback: AsyncCallback<string>): void--><!--Device-Context-getProcessName(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Return current process name. |

<a id="getprocessname-1"></a>

## getProcessName

```TypeScript
getProcessName(): Promise<string>
```

Obtains the name of the current process.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getProcessName(): Promise<string>--><!--Device-Context-getProcessName(): Promise<string>-End-->

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

<!--Device-Context-isUpdatingConfigurations(callback: AsyncCallback<boolean>): void--><!--Device-Context-isUpdatingConfigurations(callback: AsyncCallback<boolean>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | True if the configuration of the capability is being changed, otherwise false. |

<a id="isupdatingconfigurations-1"></a>

## isUpdatingConfigurations

```TypeScript
isUpdatingConfigurations(): Promise<boolean>
```

Checks whether the configuration of this ability is changing.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-isUpdatingConfigurations(): Promise<boolean>--><!--Device-Context-isUpdatingConfigurations(): Promise<boolean>-End-->

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

<!--Device-Context-printDrawnCompleted(callback: AsyncCallback<void>): void--><!--Device-Context-printDrawnCompleted(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Represents the specified callback method. |

<a id="printdrawncompleted-1"></a>

## printDrawnCompleted

```TypeScript
printDrawnCompleted(): Promise<void>
```

Inform the system of the time required for drawing this Page ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-printDrawnCompleted(): Promise<void>--><!--Device-Context-printDrawnCompleted(): Promise<void>-End-->

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

<!--Device-Context-requestPermissionsFromUser(    permissions: Array<string>,    requestCode: number,    resultCallback: AsyncCallback<PermissionRequestResult>  ): void--><!--Device-Context-requestPermissionsFromUser(    permissions: Array<string>,    requestCode: number,    resultCallback: AsyncCallback<PermissionRequestResult>  ): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permissions | Array&lt;string&gt; | Yes | Indicates the list of permissions to be requested.parameter cannot be null. |
| requestCode | number | Yes | Indicates the request code to be passed to the PermissionRequestResult |
| resultCallback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PermissionRequestResult](arkts-ability-context-permissionrequestresult-depr-i.md)&gt; | Yes | Return authorization result information. |

<a id="requestpermissionsfromuser-1"></a>

## requestPermissionsFromUser

```TypeScript
requestPermissionsFromUser(permissions: Array<string>, requestCode: number): Promise<PermissionRequestResult>
```

Requests certain permissions from the system.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-requestPermissionsFromUser(permissions: Array<string>, requestCode: number): Promise<PermissionRequestResult>--><!--Device-Context-requestPermissionsFromUser(permissions: Array<string>, requestCode: number): Promise<PermissionRequestResult>-End-->

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

<!--Device-Context-setDisplayOrientation(orientation: bundle.DisplayOrientation, callback: AsyncCallback<void>): void--><!--Device-Context-setDisplayOrientation(orientation: bundle.DisplayOrientation, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md) | Yes | Indicates the new orientation for the current ability. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the realistic direction of the screen. |

<a id="setdisplayorientation-1"></a>

## setDisplayOrientation

```TypeScript
setDisplayOrientation(orientation: bundle.DisplayOrientation): Promise<void>
```

Sets the display orientation of the current ability.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-setDisplayOrientation(orientation: bundle.DisplayOrientation): Promise<void>--><!--Device-Context-setDisplayOrientation(orientation: bundle.DisplayOrientation): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [bundle.DisplayOrientation](arkts-ability-bundle-displayorientation-e.md) | Yes | Indicates the new orientation for the current ability. |

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

<!--Device-Context-verifyPermission(permission: string, options?: PermissionOptions): Promise<number>--><!--Device-Context-verifyPermission(permission: string, options?: PermissionOptions): Promise<number>-End-->

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

<a id="verifypermission-1"></a>

## verifyPermission

```TypeScript
verifyPermission(permission: string, options: PermissionOptions, callback: AsyncCallback<number>): void
```

Verify whether the specified permission is allowed for a particular pid and uid running in the system. Pid and uid are optional. If you do not pass in pid and uid, it will check your own permission.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-verifyPermission(permission: string, options: PermissionOptions, callback: AsyncCallback<number>): void--><!--Device-Context-verifyPermission(permission: string, options: PermissionOptions, callback: AsyncCallback<number>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permission | string | Yes | The name of the specified permission |
| options | [PermissionOptions](arkts-ability-context-permissionoptions-depr-i.md) | Yes | Permission Options |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Return permission verification result, 0 has permission, -1 has no permission. |

<a id="verifypermission-2"></a>

## verifyPermission

```TypeScript
verifyPermission(permission: string, callback: AsyncCallback<number>): void
```

Verify whether the specified permission is allowed for a particular pid and uid running in the system. Pid and uid are optional. If you do not pass in pid and uid, it will check your own permission.

**Since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-verifyPermission(permission: string, callback: AsyncCallback<number>): void--><!--Device-Context-verifyPermission(permission: string, callback: AsyncCallback<number>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| permission | string | Yes | The name of the specified permission |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Return permission verification result, 0 has permission, -1 has no permission. |

## getExternalCacheDir

```TypeScript
getExternalCacheDir(callback: AsyncCallback<string>): void
```

Obtains the absolute path to the application-specific cache directory

**Since:** 6

**Deprecated since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getExternalCacheDir(callback: AsyncCallback<string>): void--><!--Device-Context-getExternalCacheDir(callback: AsyncCallback<string>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Returns the absolute path of the application's cache directory. |

<a id="getexternalcachedir-1"></a>

## getExternalCacheDir

```TypeScript
getExternalCacheDir(): Promise<string>
```

Obtains the absolute path to the application-specific cache directory

**Since:** 6

**Deprecated since:** 7

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-getExternalCacheDir(): Promise<string>--><!--Device-Context-getExternalCacheDir(): Promise<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Return the cache directory of the application. |

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(show: boolean, callback: AsyncCallback<void>): void
```

Sets whether to show this ability on top of the lock screen whenever the lock screen is displayed, keeping the ability in the ACTIVE state. The interface can only take effect in API8 and below versions.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-setShowOnLockScreen(show: boolean, callback: AsyncCallback<void>): void--><!--Device-Context-setShowOnLockScreen(show: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| show | boolean | Yes | Specifies whether to show this ability on top of the lock screen. The value true means to show it on the lock screen, and the value false means not. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Returns the callback result. |

<a id="setshowonlockscreen-1"></a>

## setShowOnLockScreen

```TypeScript
setShowOnLockScreen(show: boolean): Promise<void>
```

Sets whether to show this ability on top of the lock screen whenever the lock screen is displayed, keeping the ability in the ACTIVE state. The interface can only take effect in API8 and below versions.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-setShowOnLockScreen(show: boolean): Promise<void>--><!--Device-Context-setShowOnLockScreen(show: boolean): Promise<void>-End-->

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

<!--Device-Context-setWakeUpScreen(wakeUp: boolean, callback: AsyncCallback<void>): void--><!--Device-Context-setWakeUpScreen(wakeUp: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wakeUp | boolean | Yes | Specifies whether to wake up the screen. The value true means to wake it up, and the value false means not. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Returns the callback result. |

<a id="setwakeupscreen-1"></a>

## setWakeUpScreen

```TypeScript
setWakeUpScreen(wakeUp: boolean): Promise<void>
```

Sets whether to wake up the screen when this ability is restored.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** setWakeUpScreen

**Model restriction:** This API can be used only in the FA model.

<!--Device-Context-setWakeUpScreen(wakeUp: boolean): Promise<void>--><!--Device-Context-setWakeUpScreen(wakeUp: boolean): Promise<void>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wakeUp | boolean | Yes | Specifies whether to wake up the screen. The value true means to wake it up, and the value false means not. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |
