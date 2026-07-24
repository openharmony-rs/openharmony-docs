# @ohos.fileshare (File Sharing) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rainlost-->
<!--Designer: @rainlost-->
<!--Tester: @leiyuqian; @zsyztt; @yue-ye2-->
<!--Adviser: @jinqiuheng-->

This module provides APIs for sharing files, which allows a system app to grant the access permissions on a file in the public directory to another app based on the file Uniform Resource Identifier (URI). It also provides APIs for verifying the authorization status, as well as managing temporary and persistent authorization. The authorized app can perform operations such as open, read, and write on the file by calling the [@ohos.file.fs](js-apis-file-fs.md) APIs, implementing file sharing between system apps and access control on files in the public directory.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.fileshare (File Sharing)](js-apis-fileShare.md).

## Modules to Import

```ts
import { fileShare } from '@kit.CoreFileKit';
```

## SharedDirectoryInfo

Describes the directory shared by an app.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API. 

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

| Name | Type | Read-Only| Optional| Description                                                  |
|------|-------|------|-----|------------------------------------------------------|
| bundleName | string | Yes  | No| Bundle name of the app.                                      |
| path | string | Yes  | No| Directory shared by the app.|
| permissionMode | number | Yes  | No| Permission to share the directory by the app. The enumerated values in [OperationMode](./js-apis-fileShare.md#operationmode11) can be used. You can use multiple enumerated values to grant multiple permissions. For example, you can use **READ_MODE** and **WRITE_MODE** to grant the read and write permissions. |

## fileShare.grantUriPermission

grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags, callback: AsyncCallback&lt;void&gt;): void

Grants temporary permissions to access URIs of files in the public directory to an app. This API uses an asynchronous callback to return the result.

**Required permissions:** ohos.permission.WRITE_MEDIA 

**System API:** This is a system API. 

**System capability:** SystemCapability.FileManagement.AppFileService

**Parameters**

| Name| Type| Mandatory| Description|
| ------ |---------| ---- |-----------|
| uri   | string| Yes  | URI of the file in the public directory.|
| bundleName   | string| Yes  | Application to be granted with the permissions.  |
| flag   | [wantConstant.Flags](../apis-ability-kit/js-apis-app-ability-wantConstant.md#flags) | Yes  | Permissions to grant.    |
| callback | AsyncCallback&lt;void&gt;| Yes   | Callback used to return the result.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| ------ | ------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 14300001 | IPC error. |

**Example**

  ```ts
  import { wantConstant } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileShare } from '@kit.CoreFileKit';

  let uri: string =
    'file://docs/storage/Users/currentUser/Document/1.txt'; // You are advised to use the system API fileUri.getUriFromPath('Sandbox path') to generate a URI.
  let bundleName: string = 'com.demo.test';
  try {
    fileShare.grantUriPermission(uri, bundleName, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION |
      wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION, (err: BusinessError) => {
      if (err) {
        console.error(`grantUriPermission failed with error: ${JSON.stringify(err)}`);
        return;
      }
      console.info('grantUriPermission success!');
    });
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`grantUriPermission failed with error: ${JSON.stringify(error)}`);
  }
  ```

## fileShare.grantUriPermission

grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags): Promise&lt;void&gt;

Grants temporary permissions to access URIs of files in the public directory to an app. This API uses a promise to return the result.

**Required permissions:** ohos.permission.WRITE_MEDIA 

**System API:** This is a system API. 

**System capability:** SystemCapability.FileManagement.AppFileService 

**Parameters**

| Name| Type| Mandatory| Description       |
| ------ |-------| ---- |-----------|
| uri   | string| Yes  | URI of the file in the public directory.|
| bundleName   | string| Yes  | Application to be granted with the permissions.  |
| flag   | [wantConstant.Flags](../apis-ability-kit/js-apis-app-ability-wantConstant.md#flags) | Yes  | Permissions to grant.    |

**Return value**

  | Type                          | Description        |
  | ---------- | ---------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| ------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 14300001 | IPC error. |

**Example**

  ```ts
  import { wantConstant } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileShare } from '@kit.CoreFileKit';

  let uri: string =
    'file://docs/storage/Users/currentUser/Document/1.txt'; // You are advised to use the system API fileUri.getUriFromPath('Sandbox path') to generate a URI.
  let bundleName: string = 'com.demo.test';
  try {
    fileShare.grantUriPermission(uri, bundleName, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION |
      wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION).then(() => {
      console.info('grantUriPermission success!');
    }).catch((error: BusinessError) => {
      console.error(`grantUriPermission failed with error: ${JSON.stringify(error)}`);
    });
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error(`grantUriPermission failed with error: ${JSON.stringify(error)}`);
  }
  ```

## fileShare.checkPathPermission<sup>15+</sup>

checkPathPermission(tokenID: number, policies: Array&lt;PathPolicyInfo&gt;, policyType: PolicyType): Promise&lt;Array&lt;boolean&gt;&gt;

Checks whether temporary or persistent permissions to access the specified files or directories are available. This API uses a promise to return the result.

**Required permissions:** ohos.permission.CHECK_SANDBOX_POLICY

**System API:** This is a system API.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| tokenID| number | Yes| App token ID, which is the value of **accessTokenId** in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md).|
| policies| Array&lt;[PathPolicyInfo](js-apis-fileShare.md#pathpolicyinfo15)> | Yes| Array of policies for querying the permission status. Elements in the array correspond to the returned results. The maximum number of policies is 500.|
| policyType| [PolicyType](js-apis-fileShare.md#policytype15) | Yes| Policy type. Set this parameter to **TEMPORARY_TYPE** to query temporary permissions and **PERSISTENT_TYPE** to query persistent permissions.|

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise used to return the permission status verification result array. Elements in the array correspond to the policy elements. The value **true** means that a policy type is used; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801      | Capability not supported. |
| 13900042 | Out of memory.|

**Example**

  ```ts
  import { fileShare } from '@kit.CoreFileKit';
  
  async function checkPersistentPermissionExample() {
    try {
      let pathPolicyInfo1: fileShare.PathPolicyInfo = {
        path: '/storage/Users/currentUser/Documents/1.txt',
        operationMode: fileShare.OperationMode.READ_MODE,
      }
      let pathPolicyInfo2: fileShare.PathPolicyInfo = {
        path: '/storage/Users/currentUser/Desktop/2.txt',
        operationMode: fileShare.OperationMode.READ_MODE,
      }

      let policies: Array<fileShare.PathPolicyInfo> = [pathPolicyInfo1, pathPolicyInfo2];
      let policyType: fileShare.PolicyType = fileShare.PolicyType.PERSISTENT_TYPE;
      let tokenID = 537688848; // Use bundleManager.getApplicationInfo() to obtain the token ID for a system app, and use bundleManager.getBundleInfoForSelf() to obtain the token ID for a non-system app.

      fileShare.checkPathPermission(tokenID, policies, policyType).then((result: Array<boolean>) => {
        for (let hasPermission of result) {
          console.info('check permission result is', hasPermission);
        }
      });
      console.info('checkPathPermission finish');
    } catch (error) {
      console.info(`checkPathPermission error, Code: ${error.code}, message: ${error.message}`);
    }
  }
  ```

## fileShare.grantUriPermission<sup>20+</sup>

grantUriPermission(policies: Array&lt;PolicyInfo&gt;, targetBundleName: string, appCloneIndex: number): Promise&lt;void&gt;

Grants temporary permissions to access a file to an app. This API uses a promise to return the result. Temporary permissions can be revoked using **revokePermission** when they are no longer needed.

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System API:** This is a system API.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| policies| Array&lt;[PolicyInfo](js-apis-fileShare.md#policyinfo11)> | Yes| Array of policies for granting permissions on URIs. Elements in the array are **PolicyInfo** objects. The maximum number of policies is 500.|
| targetBundleName| string | Yes| Bundle name of the target app.|
| appCloneIndex| number | Yes| Index of the cloned app. The value **0** indicates the app itself; a non-zero value indicates a clone of the app.|

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed.|
| 202      | The caller is not a system application.|
| 801      | Capability not supported. |
| 13900001      | Operation not permitted. |
| 13900011      | Out of memory. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileShare } from '@kit.CoreFileKit';
  
  async function grantUriPermissionExample() {
    try {
      let uri = 'file://docs/storage/Users/currentUser/Documents/1.txt';
      let policyInfo: fileShare.PolicyInfo = {
        uri: uri,
        operationMode: fileShare.OperationMode.CREATE_MODE | fileShare.OperationMode.READ_MODE,
      };
      let policies: Array<fileShare.PolicyInfo> = [policyInfo];

      fileShare.grantUriPermission(policies, 'com.example.myapplicationtest', 0).then(() => {
      }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
        console.error(`grantUriPermission failed. Code: ${err.code}, message: ${err.message}`);
      });
    } catch (error) {
      console.info(`grantUriPermission error, Code: ${error.code}, message: ${error.message}`);
    }
  }
  ```

## fileShare.getSharedDirectoryInfo

getSharedDirectoryInfo(): Promise&lt;Array&lt;SharedDirectoryInfo&gt;&gt;

Obtains all sandbox directories shared by the app. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.ACCESS_SHARED_FILE

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;Array&lt;[SharedDirectoryInfo](#shareddirectoryinfo)&gt;&gt; | Promise used to return all sandbox directories shared by the app.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 801      | Capability not supported. |
| 13900001      | Operation not permitted. |
| 13900011      | Out of memory. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function getSharedDirectoryInfo() {
  try {
    fileShare.getSharedDirectoryInfo().then((infos: Array<fileShare.SharedDirectoryInfo>) => {
      infos.forEach((info: fileShare.SharedDirectoryInfo) => {
        console.info(`bundleName=${info.bundleName} path=${info.path} mode=${info.permissionMode}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`getSharedDirectoryInfo err: ${JSON.stringify(err)}`);
    });
  } catch (error) {
    console.error(`getSharedDirectoryInfo error, Code: ${error.code}, message: ${error.message}`);
  }
}
```


## fileShare.grantSharedDirectoryPermission

grantSharedDirectoryPermission(): Promise&lt;void&gt;

Grants temporary permissions to access the directory shared by an app. This API uses a promise to return the result. The temporary access permissions can be revoked using **revokeSharedDirectoryPermission**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.ACCESS_SHARED_FILE

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 801      | Capability not supported. |
| 13900001      | Operation not permitted. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function grantSharedDirectoryPermission() {
  try {
    fileShare.grantSharedDirectoryPermission().then(() => {
      console.info('grantSharedDirectoryPermission success');
    }).catch((err: BusinessError) => {
      console.error(`grantSharedDirectoryPermission err: ${JSON.stringify(err)}`);
    });
  } catch (error) {
    console.error(`grantSharedDirectoryPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

## fileShare.revokeSharedDirectoryPermission

revokeSharedDirectoryPermission(): Promise&lt;void&gt;

Revokes the temporary permissions to access the directory shared by an app. This API uses a promise to return the result. This API is used to revoke the temporary permissions to access the directory granted by **grantSharedDirectoryPermission**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API:** This is a system API.

**Required permissions:** ohos.permission.ACCESS_SHARED_FILE

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 801      | Capability not supported. |
| 13900001      | Operation not permitted. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeSharedDirectoryPermission() {
  try {
    fileShare.revokeSharedDirectoryPermission().then(() => {
      console.info('revokeSharedDirectoryPermission success');
    }).catch((err: BusinessError) => {
      console.error(`revokeSharedDirectoryPermission err: ${JSON.stringify(err)}`);
    });
  } catch (error) {
    console.error(`revokeSharedDirectoryPermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

## fileShare.revokePermission

revokePermission(tokenID: number): Promise&lt;void&gt;

Revokes all persistent permissions to access files for specified apps. This API uses a promise to return the result. To revoke persistent permissions to access a specified URI, use **revokePermission(tokenID, policies)**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.REVOKE_FILE_ACCESS_PERSIST

**System API:** This is a system API.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| tokenID| number | Yes| Token ID of the target app, which is the value of **accessTokenId** in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md) of [BundleInfo](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md).|

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 801      | Capability not supported. |
| 13900001 | Operation not permitted. |
| 13900020 | Invalid tokenID. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeAllPermissionExample() {
  try {
    let tokenID = 537688848; // Use bundleManager.getApplicationInfo() to obtain the token ID for a system app, and use bundleManager.getBundleInfoForSelf() to obtain the token ID for a non-system app.
    fileShare.revokePermission(tokenID).then(() => {
      console.info('revoke persist permission successfully.');
    }).catch((err: BusinessError) => {
      console.error(`revoke persist permission failed, Code: ${err.code}, message: ${err.message}`);
    });
  } catch (error) {
    console.error(`revoke persist permission failed error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

## fileShare.revokePermission

revokePermission(tokenID: number, policies: Array&lt;PolicyInfo&gt;): Promise&lt;void&gt;

Revokes persistent permissions to access URIs for specified apps. This API uses a promise to return the result. This method revokes permissions to access only the URIs specified by policies. To revoke all persistent permissions for a specified app, use **revokePermission(tokenID)**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.REVOKE_FILE_ACCESS_PERSIST

**System API:** This is a system API.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| tokenID| number | Yes| Token ID of the target app, which is the value of **accessTokenId** in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md) of [BundleInfo](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md).|
| policies| Array&lt;[PolicyInfo](js-apis-fileShare.md#policyinfo11)&gt; | Yes| Array of policies for revoking persistent permissions. The maximum number of policies is 500.|

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

If the permission to access some URIs fails to be revoked, error code 13900001 is returned and the **data** field provides error information of these URIs in the Array&lt;[PolicyErrorResult](js-apis-fileShare.md#policyerrorresult11)&gt; format.

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Invalid policy size.|
| 801      | Capability not supported. |
| 13900001 | Operation not permitted. |
| 13900011 | Out of memory. |
| 13900020 | Invalid tokenID. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function revokeSpecificPermissionExample() {
  try {
    let tokenID = 537688848; // Use bundleManager.getApplicationInfo() to obtain the token ID for a system app, and use bundleManager.getBundleInfoForSelf() to obtain the token ID for a non-system app.
    let policyInfo: fileShare.PolicyInfo = {
      uri: 'file://docs/storage/Users/currentUser/Documents/1.txt',
      operationMode: fileShare.OperationMode.READ_MODE | fileShare.OperationMode.WRITE_MODE,
    };
    let policies: Array<fileShare.PolicyInfo> = [policyInfo];
    fileShare.revokePermission(tokenID, policies).then(() => {
      console.info('revoke persist permission successfully.');
    }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
      console.error(`revoke persist permission failed. Code: ${err.code}, message: ${err.message}`);
      if (err.code === 13900001 && err.data) {
        for (let i = 0; i < err.data.length; i++) {
          console.error(`error code: ${JSON.stringify(err.data[i].code)}`);
          console.error(`error URI: ${JSON.stringify(err.data[i].uri)}`);
          console.error(`error reason: ${JSON.stringify(err.data[i].message)}`);
        }
      }
    });
  } catch (error) {
    console.error(`revokePermission error, Code: ${error.code}, message: ${error.message}`);
  }
}
```

## fileShare.getPersistentPolicy

getPersistentPolicy(tokenID: number): Promise&lt;Array&lt;PolicyInfo&gt;&gt;

Obtains the persistent permission policy of an app. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.GET_FILE_ACCESS_PERSIST

**System API:** This is a system API.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| tokenID| number | Yes| Token ID of the target app, which is the value of **accessTokenId** in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md) of [BundleInfo](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md).|

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;Array&lt;[PolicyInfo](js-apis-fileShare.md#policyinfo11)&gt;&gt; | Promise used to return an array of persistent policies of the app.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 801      | Capability not supported. |
| 13900001 | Operation not permitted. |
| 13900011 | Out of memory. |
| 13900020 | Invalid tokenID. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileShare } from '@kit.CoreFileKit';

async function getPersistentPolicyExample() {
  try {
    let tokenID = 537688848; // Use bundleManager.getApplicationInfo() to obtain the token ID for a system app, and use bundleManager.getBundleInfoForSelf() to obtain the token ID for a non-system app.
    fileShare.getPersistentPolicy(tokenID).then((result: Array<fileShare.PolicyInfo>) => {
      for (let policy of result) {
        console.info(`get persist policy URI: ${policy.uri}, operationMode: ${policy.operationMode}`);
      }
    }).catch((err: BusinessError) => {
      console.error(`get persist policy failed with error, Code: ${err.code}, message: ${err.message}`);
    });
  } catch (error) {
    console.error(`get persist policy failed with error, Code: ${error.code}, message: ${error.message}`);
  }
}
```
