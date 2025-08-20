# @ohos.fileshare (File Sharing) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lvzhenjie; @hongjin-li_admin-->
<!--Designer: @chenxi0605; @JerryH1011-->
<!--Tester: @leiyuqian-->
<!--Adviser: @foryourself-->

The **fileShare** module provides APIs for granting the access permissions on a user file to another application based on the file Uniform Resource Identifier (URI). Then, the authorized application can access the file by using the [@ohos.file.fs](js-apis-file-fs.md) APIs.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.fileshare](js-apis-fileShare-sys.md).

## Modules to Import

```ts
import  { fileShare } from '@kit.CoreFileKit';
```

## fileShare.grantUriPermission

grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags, callback: AsyncCallback&lt;void&gt;): void

Grants the permissions on a user file to an application. This API uses an asynchronous callback to return the result. 

**Required permissions**: ohos.permission.WRITE_MEDIA 

**System API**: This is a system API. 

**System capability**: SystemCapability.FileManagement.AppFileService

**Parameters**

| Name| Type| Mandatory| Description|
| ------ |---------| ---- |-----------|
| uri   | string| Yes  | URI of the file under user directory.|
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
| 143000001 | IPC error. |

**Example**

  ```ts
  import { wantConstant } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  let uri: string = 'file://docs/storage/Users/currentUser/Document/1.txt';  // You are advised to use the system API fileUri.getUriFromPath("Sandbox path") to generate a URI.;
  let bundleName: string = 'com.demo.test';
  try {
    fileShare.grantUriPermission(uri, bundleName, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION |
      wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION, (err: BusinessError) => {
      if (err) {
        console.error("grantUriPermission failed with error: " + JSON.stringify(err));
        return;
      }
      console.info("grantUriPermission success!");
    });
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("grantUriPermission failed with error:" + JSON.stringify(error));
  }
  ```

## fileShare.grantUriPermission

grantUriPermission(uri: string, bundleName: string, flag: wantConstant.Flags): Promise&lt;void&gt;

Grants the permissions on a user file to an application. This API uses a promise to return the result. 

**Required permissions**: ohos.permission.WRITE_MEDIA 

**System API**: This is a system API. 

**System capability**: SystemCapability.FileManagement.AppFileService 

**Parameters**

| Name| Type| Mandatory| Description       |
| ------ |-------| ---- |-----------|
| uri   | string| Yes  | URI of the file under user directory.|
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
| 143000001 | IPC error. |

**Example**

  ```ts
  import { wantConstant } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';
  let uri: string = 'file://docs/storage/Users/currentUser/Document/1.txt'; // You are advised to use the system API fileUri.getUriFromPath("Sandbox path") to generate a URI.;
  let bundleName: string = 'com.demo.test';
  try {
    fileShare.grantUriPermission(uri, bundleName, wantConstant.Flags.FLAG_AUTH_READ_URI_PERMISSION |
      wantConstant.Flags.FLAG_AUTH_WRITE_URI_PERMISSION).then(() => {
      console.info("grantUriPermission success!");
    }).catch((error: BusinessError) => {
      console.error("grantUriPermission failed with error:" + JSON.stringify(error));
    });
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("grantUriPermission failed with error:" + JSON.stringify(error));
  }
  ```

## fileShare.checkPathPermission<sup>15+</sup>

checkPathPermission(tokenID: number, policies: Array&lt;PathPolicyInfo&gt;, policyType: PolicyType): Promise&lt;Array&lt;boolean&gt;&gt;

Checks whether the selected files or directories have temporary or persistent permissions. This API uses a promise to return the result.

**Required permissions**: ohos.permission.CHECK_SANDBOX_POLICY

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| tokenID| number | Yes| Application token ID, which is the value of **accessTokenId** in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md).|
| policies| Array&lt;[PathPolicyInfo](js-apis-fileShare.md#pathpolicyinfo15)> | Yes| Array of permission policies. The maximum number of policies is 500.|
| policyType| [PolicyType](js-apis-fileShare.md#policytype15) | Yes| Policy type to check, which can be a temporary or persistent permission.|

**Return value**

|Type|Description|
| ------ | ------ |
| Promise&lt;Array&lt;boolean&gt;&gt; | Promise used to return the result. The value **true** means that a policy type is used; the value **false** means the opposite.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID   | Error Message      |
|----------| --------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.|
| 202      | The caller is not a system application.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801      | Capability not supported. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileShare } from '@kit.CoreFileKit';
  
  async function checkPersistentPermissionExample() {
    try {
      let pathPolicyInfo1: fileShare.PathPolicyInfo = {
        path: "/storage/Users/currentUser/Documents/1.txt",
        operationMode: fileShare.OperationMode.READ_MODE,
      }
      let pathPolicyInfo2: fileShare.PathPolicyInfo = {
        path: "/storage/Users/currentUser/Desktop/2.txt",
        operationMode: fileShare.OperationMode.READ_MODE,
      }

      let policies: Array<fileShare.PathPolicyInfo> = [pathPolicyInfo1, pathPolicyInfo2];
      let policyType: fileShare.PolicyType = fileShare.PolicyType.PERSISTENT_TYPE;
      let tokenid = 537688848; // Use bundleManager.getApplicationInfo() to obtain the token ID for a system application, and use bundleManager.getBundleInfoForSelf() to obtain the token ID for a non-system application.

      fileShare.checkPathPermission(tokenid, policies, policyType).then((result:Array<boolean>) => {
        for (let x of result) {
          console.info('check permission result is', x);
        }
      })
      console.info("checkPathPermission finish");
    }
    catch (error) {
      console.info(error.code + 'checkPathPermission error' + error.message);
    }
  }
  ```

## fileShare.grantUriPermission<sup>20+</sup>

grantUriPermission(policies: Array&lt;PolicyInfo&gt;, targetBundleName: string, appCloneIndex: number): Promise&lt;void&gt;

Grants temporary permissions on a file to an application. This API uses a promise to return the result.

**Required permissions**: ohos.permission.FILE_ACCESS_MANAGER

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.AppFileService.FolderAuthorization

**Parameters**

| Name| Type| Mandatory| Description|
| -------- |-------| -------- |----------|
| policies| Array&lt;[PolicyInfo](js-apis-fileShare.md#policyinfo11)> | Yes| Array of permission policies. The maximum number of policies is 500.|
| targetBundleName| string | Yes| Bundle name of the target application.|
| appCloneIndex| number | Yes| Index of the cloned application. The value **0** indicates the application itself.|

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
| 13900011      | Out of memory. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { fileShare } from '@kit.CoreFileKit';
  
  async function grantUriPermissionExample() {
    try {
      let uri = "file://docs/storage/Users/currentUser/Documents/1.txt";
      let policyInfo: fileShare.PolicyInfo = {
        uri: uri,
        operationMode: fileShare.OperationMode.CREATE_MODE | fileShare.OperationMode.READ_MODE,
      };
      let policies: Array<fileShare.PolicyInfo> = [policyInfo];

      fileShare.grantUriPermission(policies, "com.example.myapplicationtest", 0).then(() => {
      }).catch((err: BusinessError<Array<fileShare.PolicyErrorResult>>) => {
        console.error("grantUriPermission failed. Code: " +
        err.code + ", message: " + err.message);
      });
    }
    catch (error) {
      console.info('grantUriPermission error, Code: ' + error.code + ', message: ' + error.message);
    }
  }
  ```
