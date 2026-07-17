# @ohos.bundle (Bundle Module) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7eb6f57046c125c4e13d8acd776d3cbaf09f5103 translatedAt=2026-06-22T06:57:25.785Z pushedAt=2026-06-25T06:21:21.391Z -->

This module provides the capability to query app information, including [BundleInfo](js-apis-bundle-BundleInfo.md), [ApplicationInfo](js-apis-bundle-ApplicationInfo.md), [AbilityInfo](js-apis-bundle-AbilityInfo.md), and other information, as well as querying and setting the disabled status of apps.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Since API version 9, this module is no longer maintained. It is recommended that you use [Bundle Management Module](js-apis-bundleManager-sys.md) for system APIs instead.
>
> This page contains only the system APIs of this module. For other public APIs, see [Bundle Module](js-apis-Bundle.md).

## Modules to Import

```ts
import bundle from '@ohos.bundle';
```

## Required Permissions

| Permission                                        | APL        | Description           |
|--------------------------------------------|--------------|---------------|
| ohos.permission.CHANGE_ABILITY_ENABLED_STATE | system_basic | Permission to enable or disable an application or ability.|
| ohos.permission.GET_BUNDLE_INFO | normal | Permission to query information about a specified bundle.|
| ohos.permission.GET_BUNDLE_INFO_PRIVILEGED| system_basic | Permission to query information about all bundles.    |
| ohos.permission.INSTALL_BUNDLE             | system_core  | Permission to install or uninstall bundles.     |
| ohos.permission.REMOVE_CACHE_FILES | system_basic | Permission to clear cache files of a bundle.|

For details about the APL, see [Basic Concepts in the Permission Mechanism](../../security/AccessToken/app-permission-mgmt-overview.md#basic-concepts-in-the-permission-mechanism).

## bundle.getBundleInstaller<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [installer.getBundleInstaller](js-apis-installer-sys.md#bundleinstallergetbundleinstaller) instead.

getBundleInstaller(): Promise&lt;BundleInstaller&gt;

Obtains the installation package. This API uses a promise to return the result.

**Required permissions**

ohos.permission.INSTALL_BUNDLE

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Return value**

| Type                                                        | Description                                        |
| ------------------------------------------------------------ | -------------------------------------------- |
| Promise<[BundleInstaller](js-apis-bundle-BundleInstaller-sys.md)> | Promise used to return the installation package.|

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

bundle.getBundleInstaller().then((data) => {
  console.info('getBundleInstaller successfully.');
}).catch((error: BusinessError) => {
  console.error('getBundleInstaller failed.');
});
```

## bundle.getBundleInstaller<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [installer.getBundleInstaller](js-apis-installer-sys.md#bundleinstallergetbundleinstaller) instead.

getBundleInstaller(callback: AsyncCallback&lt;BundleInstaller&gt;): void

Obtains the installation package. This API uses an asynchronous callback to return the result.

**Required permissions**

ohos.permission.INSTALL_BUNDLE

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name  | Type                                                        | Mandatory| Description            |
| -------- | ------------------------------------------------------------ | ---- | ---------------- |
| callback | AsyncCallback<[BundleInstaller](js-apis-bundle-BundleInstaller-sys.md)> | Yes  | Callback used to return the installation package.|

**Example**

```ts
import bundle from '@ohos.bundle';

bundle.getBundleInstaller((err, data) => {
  if (err.code == 0) {
    console.error('getBundleInstaller successfully.');
  } else {
    console.info('getBundleInstaller failed.');
  }
});
```

## bundle.cleanBundleCacheFiles<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [cleanBundleCacheFiles](js-apis-bundleManager-sys.md#bundlemanagercleanbundlecachefiles) instead.

cleanBundleCacheFiles(bundleName: string, callback: AsyncCallback&lt;void&gt;): void

Clears the cache data of an application. This API uses an asynchronous callback to return the result.

**Required permissions**

ohos.permission.REMOVE_CACHE_FILES

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name     | Type               | Mandatory| Description                                 |
| ---------- | ------------------- | ---- | ------------------------------------- |
| bundleName | string              | Yes  | Bundle name.|
| callback   | AsyncCallback\<void> | Yes  | Callback used to return the result.         |

**Example**

```ts
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";

bundle.cleanBundleCacheFiles(bundleName, err => {
  if (err) {
    console.error('cleanBundleCacheFiles failed.');
  } else {
    console.info('cleanBundleCacheFiles successfully.');
  }
});
```

## bundle.cleanBundleCacheFiles<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [cleanBundleCacheFiles](js-apis-bundleManager-sys.md#bundlemanagercleanbundlecachefiles) instead.

cleanBundleCacheFiles(bundleName: string): Promise&lt;void&gt;

Clears the cache data of an application. This API uses a promise to return the result.

**Required permissions**

ohos.permission.REMOVE_CACHE_FILES

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name    | Type  | Mandatory| Description                                 |
| ---------- | ------ | ---- | ------------------------------------- |
| bundleName | string | Yes  | Bundle name.|

**Return value**

| Type         | Description                                |
| ------------- | ------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";

bundle.cleanBundleCacheFiles(bundleName).then(() => {
  console.info('cleanBundleCacheFiles successfully.');
}).catch((error: BusinessError) => {
  console.error('cleanBundleCacheFiles failed.');
});
```

## bundle.setApplicationEnabled<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [setApplicationEnabled](js-apis-bundleManager-sys.md#bundlemanagersetapplicationenabled) instead.

setApplicationEnabled(bundleName: string, isEnable: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether to enable an application. This API uses an asynchronous callback to return the result.

**Required permissions**

ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name     | Type               | Mandatory| Description                            |
| ---------- | ------------------- | ---- |--------------------------------|
| bundleName | string              | Yes  | Bundle name.         |
| isEnable   | boolean             | Yes  | Whether to enable the application. **true** to enable, **false** otherwise.|
| callback   | AsyncCallback\<void> | Yes  | Callback used to return the result.                         |

**Example**

```ts
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";

bundle.setApplicationEnabled(bundleName, false, err => {
  if (err) {
    console.error('setApplicationEnabled failed.');
  } else {
    console.info('setApplicationEnabled successfully.');
  }
});
```

## bundle.setApplicationEnabled<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [setApplicationEnabled](js-apis-bundleManager-sys.md#bundlemanagersetapplicationenabled) instead.

setApplicationEnabled(bundleName: string, isEnable: boolean): Promise&lt;void&gt;

Sets whether to enable an application. This API uses a promise to return the result.

**Required permissions**

ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name    | Type   | Mandatory| Description                                           |
| ---------- | ------- | ---- | ----------------------------------------------- |
| bundleName | string  | Yes  | Bundle name.           |
| isEnable   | boolean | Yes  | Whether to enable the application. **true** to enable, **false** otherwise.|

**Return value**

| Type         | Description                                |
| ------------- | ------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";

bundle.setApplicationEnabled(bundleName, false).then(() => {
  console.info('setApplicationEnabled successfully.');
}).catch((error: BusinessError) => {
  console.error('setApplicationEnabled failed.');
});
```

## bundle.setAbilityEnabled<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [setAbilityEnabled](js-apis-bundleManager-sys.md#bundlemanagersetabilityenabled) instead.

setAbilityEnabled(info: AbilityInfo, isEnable: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether to enable an ability. This API uses an asynchronous callback to return the result.

**Required permissions**

ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name  | Type                                        | Mandatory| Description                                           |
| -------- | -------------------------------------------- | ---- | ----------------------------------------------- |
| info     | [AbilityInfo](js-apis-bundle-AbilityInfo.md) | Yes  | Ability information.                                  |
| isEnable | boolean                                      | Yes  | Whether to enable the application. **true** to enable, **false** otherwise.|
| callback | AsyncCallback\<void>                         | Yes  | Callback used to return the result.                   |

## bundle.setAbilityEnabled<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [setAbilityEnabled](js-apis-bundleManager-sys.md#bundlemanagersetabilityenabled) instead.

setAbilityEnabled(info: AbilityInfo, isEnable: boolean): Promise&lt;void&gt;

Sets whether to enable an ability. This API uses a promise to return the result.

**Required permissions**

ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name  | Type                                        | Mandatory| Description                                           |
| -------- | -------------------------------------------- | ---- | ----------------------------------------------- |
| info     | [AbilityInfo](js-apis-bundle-AbilityInfo.md) | Yes  | Ability information.                                  |
| isEnable | boolean                                      | Yes  | Whether to enable the application. **true** to enable, **false** otherwise.|

**Return value**

| Type         | Description                                |
| ------------- | ------------------------------------ |
| Promise\<void> | Promise that returns no value.|

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityInfo(bundleName, abilityName).then((abilityInfo) => {
  console.info('getAbilityInfo successfully. Data: ' + JSON.stringify(abilityInfo));

  bundle.setAbilityEnabled(abilityInfo, false).then(data => {
    console.info('setAbilityEnabled successfully.');
  }).catch((error: BusinessError) => {
    console.error('setAbilityEnabled failed:' + JSON.stringify(error));
  })
}).catch((error: BusinessError) => {
  console.error('getAbilityInfo failed. Cause: ' + JSON.stringify(error));
});
```

## bundle.getPermissionDef<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [getPermissionDef](js-apis-bundleManager-sys.md#bundlemanagergetpermissiondef) instead.

getPermissionDef(permissionName: string, callback: AsyncCallback&lt;PermissionDef&gt;): void

Obtains the permission details by permission name. This API uses an asynchronous callback to return the result.

**Required permissions**

ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name        | Type                                                        | Mandatory| Description                                            |
| -------------- | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| permissionName | string                                                       | Yes  | Name of the permission.                                |
| callback       | AsyncCallback<[PermissionDef](js-apis-bundle-PermissionDef-sys.md)> | Yes  | Callback used to return the permission details.|

**Example**

```ts
import bundle from '@ohos.bundle';

let permission: string = "ohos.permission.GET_BUNDLE_INFO";
bundle.getPermissionDef(permission, (err, data) => {
  if (err) {
    console.error('getPermissionDef failed:' + err.message);
  } else {
    console.info('getPermissionDef successfully:' + JSON.stringify(data));
  }
});
```

## bundle.getPermissionDef<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [getPermissionDef](js-apis-bundleManager-sys.md#bundlemanagergetpermissiondef) instead.

getPermissionDef(permissionName: string): Promise&lt;PermissionDef&gt;

Obtains the permission details by permission name. This API uses a promise to return the result.

**Required permissions**

ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability**

SystemCapability.BundleManager.BundleFramework

**System API**

This is a system API.

**Parameters**

| Name        | Type  | Mandatory| Description            |
| -------------- | ------ | ---- | ---------------- |
| permissionName | string | Yes  | Name of the permission.|

**Return value**

| Type                                                  | Description                                                  |
| ------------------------------------------------------ | ------------------------------------------------------ |
| Promise<[PermissionDef](js-apis-bundle-PermissionDef-sys.md)> | Promise used to return the permission details.|

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let permissionName: string = "ohos.permission.GET_BUNDLE_INFO";
bundle.getPermissionDef(permissionName).then((data) => {
  console.info('getPermissionDef successfully. Data: ' + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error('getPermissionDef failed. Cause: ' + error.message);
});
```

## bundle.getBundleInfos<sup>deprecated</sup>

getBundleInfos(bundleFlag: BundleFlag, userId?: number): Promise\<Array\<BundleInfo\>\>

Obtains all [BundleInfo](js-apis-bundle-BundleInfo.md) for a specified user. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [bundleManager.getAllBundleInfo](js-apis-bundleManager-sys.md#bundlemanagergetallbundleinfo-2) instead.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters**

| Name     | Type       | Mandatory | Description                                                         |
| ---------- | ---------- | ---- | ------------------------------------------------------------ |
| bundleFlag | BundleFlag | Yes   | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](js-apis-Bundle.md#bundleflagdeprecated). |
| userId     | number     | No   | User ID.<br/>Default value: the user to which the caller belongs. Value range: greater than or equal to 0.        |

**Return value**

| Type                          | Description                         |
| --------------------------- | -------------------------- |
| Promise<Array\<[BundleInfo](js-apis-bundle-BundleInfo.md)>> | Promise used to return all available [BundleInfo](js-apis-bundle-BundleInfo.md). |

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleFlag: number = bundle.BundleFlag.GET_BUNDLE_DEFAULT;
let userId: number = 100;

bundle.getBundleInfos(bundleFlag, userId)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

## bundle.getBundleInfos<sup>deprecated</sup>

getBundleInfos(bundleFlag: BundleFlag, callback: AsyncCallback\<Array\<BundleInfo\>\>): void

Obtains all [BundleInfo](js-apis-bundle-BundleInfo.md) for the current user. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [bundleManager.getAllBundleInfo](js-apis-bundleManager-sys.md#bundlemanagergetallbundleinfo-1) instead.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| bundleFlag | BundleFlag                                                   | Yes   | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](js-apis-Bundle.md#bundleflagdeprecated). |
| callback   | AsyncCallback<Array\<[BundleInfo](js-apis-bundle-BundleInfo.md)>> | Yes   | Callback used to return all available [BundleInfo](js-apis-bundle-BundleInfo.md) as the input parameter at program startup.      |

**Example**

```ts
import bundle from '@ohos.bundle';

let bundleFlag: number = bundle.BundleFlag.GET_BUNDLE_DEFAULT;

bundle.getBundleInfos(bundleFlag, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

## bundle.getBundleInfos<sup>deprecated</sup>

getBundleInfos(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback\<Array\<BundleInfo\>\>): void

Obtains all [BundleInfo](js-apis-bundle-BundleInfo.md) for a specified user in the system. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [bundleManager.getAllBundleInfo](js-apis-bundleManager-sys.md#bundlemanagergetallbundleinfo) instead.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters**

| Name        | Type                                                                | Mandatory  | Description                                                                  |
|------------|-------------------------------------------------------------------|-----|---------------------------------------------------------------------|
| bundleFlag | BundleFlag                                                        | Yes   | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](js-apis-Bundle.md#bundleflagdeprecated). |
| userId     | number                                                            | Yes   | User ID.<br/>Value range: greater than or equal to 0.                           |
| callback   | AsyncCallback<Array\<[BundleInfo](js-apis-bundle-BundleInfo.md)>> | Yes   | Callback used to return the [BundleInfo](js-apis-bundle-BundleInfo.md) of all bundles under the specified user as the input parameter at program startup.                  |

**Example**

```ts
import bundle from '@ohos.bundle';

let bundleFlag: number = bundle.BundleFlag.GET_BUNDLE_DEFAULT;
let userId: number = 100;

bundle.getBundleInfos(bundleFlag, userId, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

## bundle.getApplicationInfos<sup>deprecated</sup>

getApplicationInfos(bundleFlags: number, userId?: number): Promise\<Array\<ApplicationInfo\>\>

Obtains information about all installed apps for a specified user. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [bundleManager.getAllApplicationInfo](js-apis-bundleManager-sys.md#bundlemanagergetallapplicationinfo-2) instead.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters**

| Name      | Type   | Mandatory | Description                                                         |
| ----------- | ------ | ---- | ------------------------------------------------------------ |
| bundleFlags | number | Yes   | Flag used to specify the information contained in the returned application information object. Value range: see the application information related flags in [BundleFlag](js-apis-Bundle.md#bundleflagdeprecated). |
| userId      | number | No   | User ID.<br/>Default value: the user to which the caller belongs. Value range: greater than or equal to 0.        |

**Return value**

| Type                               | Description                              |
| -------------------------------- | ------------------------------- |
| Promise<Array\<[ApplicationInfo](js-apis-bundle-ApplicationInfo.md)>> | Promise used to return the list of app information when obtained successfully. |

**Example**

```ts
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleFlags: number = bundle.BundleFlag.GET_APPLICATION_INFO_WITH_PERMISSION;
let userId: number = 100;

bundle.getApplicationInfos(bundleFlags, userId)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

## bundle.getApplicationInfos<sup>deprecated</sup>

getApplicationInfos(bundleFlags: number, userId: number, callback: AsyncCallback\<Array\<ApplicationInfo\>\>): void

Obtains information about all installed apps for a specified user. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [bundleManager.getAllApplicationInfo](js-apis-bundleManager-sys.md#bundlemanagergetallapplicationinfo) instead.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters**

| Name      | Type                                                         | Mandatory | Description                                                         |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| bundleFlags | number                                                       | Yes   | Flag used to specify the information contained in the returned application information object. Value range: see the application information related flags in [BundleFlag](js-apis-Bundle.md#bundleflagdeprecated). |
| userId      | number                                                       | Yes   | User ID.<br/>Value range: greater than or equal to 0.        |
| callback    | AsyncCallback<Array\<[ApplicationInfo](js-apis-bundle-ApplicationInfo.md)>> | Yes   | Callback used to return the list of app information as the input parameter at program startup.               |

**Example**

```ts
import bundle from '@ohos.bundle';

let bundleFlags: number = bundle.BundleFlag.GET_APPLICATION_INFO_WITH_PERMISSION;
let userId: number = 100;

bundle.getApplicationInfos(bundleFlags, userId, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

## bundle.getApplicationInfos<sup>deprecated</sup>

getApplicationInfos(bundleFlags: number, callback: AsyncCallback\<Array\<ApplicationInfo\>\>): void

Obtains information about installed apps for the user to which the caller belongs. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [bundleManager.getAllApplicationInfo](js-apis-bundleManager-sys.md#bundlemanagergetallapplicationinfo-1) instead.

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters**

| Name      | Type                                                         | Mandatory | Description                                                         |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| bundleFlags | number                                                       | Yes   | Flag used to specify the information contained in the returned application information object. Value range: see the application information related flags in [BundleFlag](js-apis-Bundle.md#bundleflagdeprecated). |
| callback    | AsyncCallback<Array\<[ApplicationInfo](js-apis-bundle-ApplicationInfo.md)>> | Yes   | Callback used to return the list of app information as the input parameter at program startup.               |

**Example**

```ts
import bundle from '@ohos.bundle';

let bundleFlags: number = bundle.BundleFlag.GET_APPLICATION_INFO_WITH_PERMISSION;

bundle.getApplicationInfos(bundleFlags, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

## ModuleRemoveFlag<sup>deprecated</sup>

Flag indicating whether a module is associated with a widget or shortcut when it is removed.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. There is no alternative API.

**System API:** This is a system API.

**System capability:** SystemCapability.BundleManager.BundleFramework

| Name | Value | Description |
| ---------- | ---- | -------- |
| FLAG_MODULE_NOT_USED_BY_FORM | 0 | Not used by a widget. |
| FLAG_MODULE_USED_BY_FORM | 1 | Used by a widget. |
| FLAG_MODULE_NOT_USED_BY_SHORTCUT | 2 | Not used by a shortcut. |
| FLAG_MODULE_USED_BY_SHORTCUT | 3 | Used by a shortcut. |

## SignatureCompareResult<sup>deprecated</sup>

Signature verification result.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. There is no alternative API.

**System API:** This is a system API.

**System capability:** SystemCapability.BundleManager.BundleFramework

| Name | Value | Description |
| ---------- | ---- | -------- |
| SIGNATURE_MATCHED | 0 | Signatures match. |
| SIGNATURE_NOT_MATCHED | 1 | Signatures do not match. |
| SIGNATURE_UNKNOWN_BUNDLE | 2 | The bundle corresponding to the signature is unknown. |

## ShortcutExistence<sup>deprecated</sup>

Result returned when querying whether a shortcut exists.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. There is no alternative API.

**System API:** This is a system API.

**System capability:** SystemCapability.BundleManager.BundleFramework

| Name | Value | Description |
| ---------- | ---- | -------- |
| SHORTCUT_EXISTENCE_EXISTS | 0 | Exists. |
| SHORTCUT_EXISTENCE_NOT_EXISTS | 1 | Does not exist. |
| SHORTCUT_EXISTENCE_UNKNOW | 2 | Unknown. |

## QueryShortCutFlag<sup>deprecated</sup>

Flag used to specify the query scope for shortcuts.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 10. There is no alternative API.

**System API:** This is a system API.

**System capability:** SystemCapability.BundleManager.BundleFramework

| Name | Value | Description |
| ---------- | ---- | -------- |
| QUERY_SHORTCUT_HOME | 0 | Query home screen shortcuts.|