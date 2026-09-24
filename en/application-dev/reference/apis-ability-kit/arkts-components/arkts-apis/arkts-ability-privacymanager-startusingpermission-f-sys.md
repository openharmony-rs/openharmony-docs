# startUsingPermission (System API)

## Modules to Import

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## startUsingPermission

```TypeScript
function startUsingPermission(tokenID: number, permissionName: Permissions): Promise<void>
```

A system application can call this API to report the application's permission usage status in the foreground or background to the system. The privacy service notifies all subscribers of this permission usage status change event (refer to [on](arkts-ability-privacymanager-on-f-sys.md) for the subscription method). This API uses a promise to return the result.

After starting to use a permission, [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) must be called to stop using the permission when the usage ends.

**Since:** 9

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenID | number | Yes | Identity identifier of the target application. It can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field in ApplicationInfo of BundleInfo. Passing an invalid value returns error code 12100001. <br>The value should be an integer. Value constraint: This parameter must be an integer greater than 0. <br>For BundleInfo acquisition, please refer to: [bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md). |
| permissionName | [Permissions](arkts-ability-permissions-t.md) | Yes | Name of the permission to be used. Passing an invalid value returns error code 12100001.<br>Value constraint: The permission name length cannot exceed 256 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256 characters, or the type of the specified tokenID is not of the application type. |
| [12100002](../errorcode-access-token.md#12100002-tokenid-not-exist) | (Deprecated in 12) The specified tokenID does not exist or refer to an application process. |
| [12100003](../errorcode-access-token.md#12100003-permission-not-exist) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | The API is used repeatedly with the same input. It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-out-of-memory) | Out of memory. |

**Examples**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: number = 0; // Obtained from the accessTokenId field of ApplicationInfo in the BundleInfo of the application.
// Start using specified permission
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```


<a id="startusingpermission-1"></a>

## startUsingPermission

```TypeScript
function startUsingPermission(
    tokenID: number,
    permissionName: Permissions,
    pid?: number,
    usedType?: PermissionUsedType
  ): Promise<void>
```

A system application can call this API to report the application's permission usage status in the foreground or background to the system. The privacy service notifies all subscribers of this permission usage status change event (refer to [on](arkts-ability-privacymanager-on-f-sys.md) for the subscription method). This API uses a promise to return the result.

After starting to use a permission, [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) must be called to stop using the permission when the usage ends.

**Since:** 18

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenID | number | Yes | Identity identifier of the target application. It can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field in ApplicationInfo of BundleInfo. Passing an invalid value returns error code 12100001. <br>The value should be an integer. Value constraint: This parameter must be an integer greater than 0. <br>For BundleInfo acquisition, please refer to: [bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md). |
| permissionName | [Permissions](arkts-ability-permissions-t.md) | Yes | Name of the permission to be used. Passing an invalid value returns error code 12100001.<br>Value constraint: The permission name length cannot exceed 256 characters. |
| pid | number | No | Process PID of the caller, used to manage the permission usage status based on the process lifecycle. Pass this parameter when you need to precisely control the permission usage status of a specific process (for example, automatically stopping permission usage when the process exits). It must be the same as the pid passed to [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md). <br>The value should be an integer. Default value: -1, indicating no response based on the process lifecycle. |
| usedType | [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md) | No | Access mode for the sensitive permission.<br>Default value: NORMAL_TYPE. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256 characters, the type of the specified tokenID is not of the application type, or usedType is invalid. |
| [12100003](../errorcode-access-token.md#12100003-permission-not-exist) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | The API is used repeatedly with the same input. It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-out-of-memory) | Out of memory. |

**Examples**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let tokenID: number = rpc.IPCSkeleton.getCallingTokenId(); // It can also be obtained from the accessTokenId field of ApplicationInfo in the BundleInfo of the application.
let pid: number = rpc.IPCSkeleton.getCallingPid();
let usedType: privacyManager.PermissionUsedType = privacyManager.PermissionUsedType.PICKER_TYPE;

// Start using a specified permission
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// with pid
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// with usedType
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', -1, usedType).then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// with pid and usedType
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, usedType).then(() => {
  console.info('startUsingPermission success');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```


<a id="startusingpermission-2"></a>

## startUsingPermission

```TypeScript
function startUsingPermission(
     tokenID: number,
     permissionName: Permissions,
     pid?: number,
     usedType?: PermissionUsedType,
     options?: PermissionUsingOptions
   ): Promise<void>
```

A system application can call this API to report the application's permission usage status in the foreground or background to the system. The privacy service notifies all subscribers of this permission usage status change event (refer to [on](arkts-ability-privacymanager-on-f-sys.md) for the subscription method). This API uses a promise to return the result.

After starting to use a permission, [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) must be called to stop using the permission when the usage ends.

When a pid is passed in, the pid must be the same as the pid passed into [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md). If the pairing relationship is not satisfied, error code 12100004 is returned.

**Since:** 26.0.0

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenID | number | Yes | Identity identifier of the target application. It can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field in ApplicationInfo of BundleInfo. Passing an invalid value returns error code 12100001. <br>The value should be an integer. Value constraint: This parameter must be an integer greater than 0. <br>For BundleInfo acquisition, please refer to: [bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md). |
| permissionName | [Permissions](arkts-ability-permissions-t.md) | Yes | Name of the permission to be used. Passing an invalid value returns error code 12100001.<br>Value constraint: The permission name length cannot exceed 256 characters. |
| pid | number | No | Process PID of the caller, used to manage the permission usage status based on the process lifecycle. Pass this parameter when you need to precisely control the permission usage status of a specific process (for example, automatically stopping permission usage when the process exits). It must be the same as the pid passed to [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md). <br>The value should be an integer. Default value: -1, indicating no response based on the process lifecycle. |
| usedType | [PermissionUsedType](arkts-ability-privacymanager-permissionusedtype-e-sys.md) | No | Access mode for the sensitive permission.<br>Default value: NORMAL_TYPE. |
| options | [PermissionUsingOptions](arkts-ability-privacymanager-permissionusingoptions-i-sys.md) | No | Optional parameter for permission usage, used to specify the extension identity. This parameter is passed in when the caller's extension identity information needs to be identified. <br>Default value: Please refer to [PermissionUsingOptions](arkts-ability-privacymanager-permissionusingoptions-i-sys.md) for the default values of each property in the structure. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256 characters, the type of the specified tokenID is not of the application type, usedType is invalid, or the enhancedIdentity in PermissionUsingOptions exceeds 48 characters. |
| [12100003](../errorcode-access-token.md#12100003-permission-not-exist) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | The API is used repeatedly with the same input. It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-out-of-memory) | Out of memory. |

**Examples**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

let tokenID: number = rpc.IPCSkeleton.getCallingTokenId(); // It can also be obtained from the accessTokenId field of ApplicationInfo in the BundleInfo of the application.
let pid: number = rpc.IPCSkeleton.getCallingPid();
let usedType: privacyManager.PermissionUsedType = privacyManager.PermissionUsedType.PICKER_TYPE;

// Without the pid and usedType parameters
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO').then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// With the pid parameter
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// With the usedType parameter
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', -1, usedType).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// With the pid and usedType parameters
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, usedType).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
// With pid, usedType, and enhancedIdentity
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', pid, usedType, {enhancedIdentity: 'test'}).then(() => {
  console.info('startUsingPermission success.');
}).catch((err: BusinessError): void => {
  console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
});
```


<a id="startusingpermission-3"></a>

## startUsingPermission

```TypeScript
function startUsingPermission(
    tokenID: number,
    permissionName: Permissions,
    callback: AsyncCallback<void>
  ): void
```

A system application can call this API to report the application's permission usage status in the foreground or background to the system. The privacy service notifies all subscribers of this permission usage status change event (refer to [on](arkts-ability-privacymanager-on-f-sys.md) for the subscription method). This API uses an asynchronous callback to return the result.

After starting to use a permission, [stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md) must be called to stop using the permission when the usage ends.

**Since:** 9

**Required permissions:** ohos.permission.PERMISSION_USED_STATS

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tokenID | number | Yes | Identity identifier of the target application. It can be obtained through the [accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid) field in ApplicationInfo of BundleInfo. Passing an invalid value returns error code 12100001. <br>The value should be an integer. Value constraint: This parameter must be an integer greater than 0. <br>For BundleInfo acquisition, please refer to: [bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md). |
| permissionName | [Permissions](arkts-ability-permissions-t.md) | Yes | Name of the permission to be used. Passing an invalid value returns error code 12100001.<br>Value constraint: The permission name length cannot exceed 256 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. Interface caller does not have permission"ohos.permission.PERMISSION_USED_STATS". |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system app. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-invalid-parameters) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256 characters, or the type of the specified tokenID is not of the application type. |
| [12100002](../errorcode-access-token.md#12100002-tokenid-not-exist) | (Deprecated in 12) The specified tokenID does not exist or refer to an application process. |
| [12100003](../errorcode-access-token.md#12100003-permission-not-exist) | The specified permission does not exist or is not a user_grant permission. |
| [12100004](../errorcode-access-token.md#12100004-listener-apis-not-used-in-pairs) | The API is used repeatedly with the same input. It means the application specified by the tokenID has been using the specified permission. |
| [12100007](../errorcode-access-token.md#12100007-system-service-not-working-properly) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-out-of-memory) | Out of memory. |

**Examples**

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tokenID: number = 0; // Obtained from the accessTokenId field of ApplicationInfo in the BundleInfo of the application.
// Start using the specified permission
privacyManager.startUsingPermission(tokenID, 'ohos.permission.READ_AUDIO', (err: BusinessError, data: void) => {
  if (err) {
    console.error(`startUsingPermission fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('startUsingPermission success');
  }
});
```
