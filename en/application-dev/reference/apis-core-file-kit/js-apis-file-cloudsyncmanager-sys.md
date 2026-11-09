# @ohos.file.cloudSyncManager (Device-Cloud Sync Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @reminder2352-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=b485e0a7070e3ab71efde69376bb2fde9696c0bc translatedAt=2026-11-03T04:18:45.300Z pushedAt=2026-11-04T05:51:53.195Z nl=1 -->

This module provides End-Cloud Synchronization Management Capability to cloud drive management applications, including enabling/disabling end-cloud collaboration capability, modifying application synchronization switches, cloud data change notification, cleaning or retaining cloud-related files upon account logout, and Full Download. Developers can use this module in cloud drive management applications to manage application End-Cloud Collaboration switches, synchronize cloud data changes, handle local cloud data after account logout, and perform Full Download and migration of cloud files.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.file.cloudSyncManager (Device-Cloud Synchronization Management)](js-apis-file-cloudsyncmanager.md).

## Modules to Import

```ts
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## cloudSyncManager.changeAppCloudSwitch

changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean): Promise&lt;void&gt;

Asynchronous Method to modify the End-Cloud file synchronization switch of an application. It applies to the scenario where the cloud synchronization capability needs to be turned on or off for a specified application. It uses a Promise asynchronous callback.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| bundleName | string | Yes  | Bundle name.|
| status | boolean | Yes  | State of the cloud-device file sync switch to set. The value **true** means to enable this function; the value **false** means the opposite.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true).then(() => {
  console.info("changeAppCloudSwitch successfully");
}).catch((err: BusinessError) => {
  console.error(`changeAppCloudSwitch failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.changeAppCloudSwitch

changeAppCloudSwitch(accountId: string, bundleName: string, status: boolean, callback: AsyncCallback&lt;void&gt;): void

Asynchronous Method to modify the End-Cloud file synchronization switch of an application. It applies to the scenario where the cloud synchronization capability needs to be turned on or off for a specified application. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| bundleName | string | Yes | Pointer to the application bundle name. |
| status | boolean | Yes  | State of the cloud-device file sync switch to set. The value **true** means to enable this function; the value **false** means the opposite.|
| callback | AsyncCallback&lt;void&gt; | Yes | Callback Function. Callback for the result of asynchronously modifying the application's end-cloud file synchronization switch. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.changeAppCloudSwitch(accountId, bundleName, true, (err: BusinessError) => {
  if (err) {
    console.error(`changeAppCloudSwitch failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("changeAppCloudSwitch successfully");
  }
});
```

## cloudSyncManager.notifyDataChange

notifyDataChange(accountId: string, bundleName: string): Promise&lt;void&gt;

Notifies the end-cloud service that the cloud data of a specific application under a specified account has changed. It applies to the scenario where the end-cloud service needs to be actively notified to synchronize changes after the application's cloud data changes. It uses a Promise asynchronous callback.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| bundleName | string | Yes  | Bundle name.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.notifyDataChange(accountId, bundleName).then(() => {
  console.info("notifyDataChange successfully");
}).catch((err: BusinessError) => {
  console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.notifyDataChange

notifyDataChange(accountId: string, bundleName: string, callback: AsyncCallback&lt;void&gt;): void

Notifies the end-cloud service that the cloud data of a specific application under a specified account has changed. It applies to the scenario where the end-cloud service needs to be actively notified to synchronize changes after the application's cloud data changes. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes   | Account ID. |
| bundleName | string | Yes  | Bundle name.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback function. Callback used to asynchronously notify the end-cloud service of the result after the application's cloud data change. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let bundleName: string = "com.example.bundle";
cloudSyncManager.notifyDataChange(accountId, bundleName, (err: BusinessError) => {
  if (err) {
    console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("notifyDataChange successfully");
  }
});
```

## ExtraData<sup>11+</sup>

Represents the cloud data change information.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name    | Type  | Read-Only| Optional| Description|
| ---------- | ------ | ---- | ---- | ---- |
| eventId | string | No   | No   | Change event ID.|
| extraData | string | No  | No  | Represents the cloud data change information.|

## cloudSyncManager.notifyDataChange<sup>11+</sup>

notifyDataChange(userId: number, extraData: ExtraData): Promise&lt;void&gt;

Notifies the device-cloud service of the cloud data change information of a specified user. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| userId | number | Yes | User ID. |
| extraData | [ExtraData](#extradata11) | Yes | Represents the cloud data change information. |

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. Possible causes: 1. IPC failed or timed out. 2. Failed to load the service. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extraData: cloudSyncManager.ExtraData = {eventId: "eventId", extraData: "data"};
cloudSyncManager.notifyDataChange(userId, extraData).then(() => {
  console.info("notifyDataChange successfully");
}).catch((err: BusinessError) => {
  console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.notifyDataChange<sup>11+</sup>

notifyDataChange(userId: number, extraData: ExtraData, callback: AsyncCallback&lt;void&gt;): void

Notifies the device-cloud service of the cloud data change information of a specified user. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| userId | number | Yes | User ID. |
| extraData | [ExtraData](#extradata11) | Yes | Represents the cloud data change information. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. Asynchronously notifies the result callback after the end-cloud service application's cloud data change. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken. |
| 202 | Permission verification failed, application which is not a system application uses system API. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001  | IPC error. Possible causes: 1. IPC failed or timed out. 2. Failed to load the service. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let userId: number = 100;
let extraData: cloudSyncManager.ExtraData = {eventId: "eventId", extraData: "data"};
cloudSyncManager.notifyDataChange(userId, extraData, (err: BusinessError) => {
  if (err) {
    console.error(`notifyDataChange failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("notifyDataChange successfully");
  }
});
```

## cloudSyncManager.enableCloud

enableCloud(accountId: string, switches: Record<string, boolean>): Promise&lt;void&gt;

Describes an asynchronous method to able the end-cloud collaboration capability. It applies to the scenario where the end-cloud collaboration capability of applications under a specified account needs to be enabled, and can be Used Together with [disableCloud](#cloudsyncmanagerdisablecloud). It uses a Promise asynchronous callback.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| switches | Record<string, boolean> | Yes  | Whether to enable the device-cloud sync feature. The application bundle name is a string. The switch status is a Boolean value. The value **true** means to enable this function; the value **false** means the opposite.|

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches).then(() => {
  console.info("enableCloud successfully.");
}).catch((err: BusinessError) => {
  console.error(`enableCloud failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.enableCloud

enableCloud(accountId: string, switches: Record<string, boolean>, callback: AsyncCallback&lt;void&gt;): void

Describes an asynchronous method to able the end-cloud collaboration capability. It applies to the scenario where the end-cloud collaboration capability of applications under a specified account needs to be enabled, and can be Used Together with [disableCloud](#cloudsyncmanagerdisablecloud). This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| switches | Record<string, boolean> | Yes  | Whether to enable the device-cloud sync feature. The application bundle name is a string. The switch status is a Boolean value. The value **true** means to enable this function; the value **false** means the opposite.|
| callback | AsyncCallback&lt;void&gt; | Yes | Callback used to return the result of asynchronously enabling the end-cloud collaboration capability. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let switches: Record<string, boolean> = {
  'com.example.bundleName1': true,
  'com.example.bundleName2': false
}
cloudSyncManager.enableCloud(accountId, switches, (err: BusinessError) => {
  if (err) {
    console.error(`enableCloud failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("enableCloud successfully");
  }
});
```

## cloudSyncManager.disableCloud

disableCloud(accountId: string): Promise&lt;void&gt;

Describes an asynchronous method to disable the end-cloud collaboration capability.It applies to the scenario where the end-cloud collaboration capability of applications under a specified account needs to be disabled, and can be Used Together with [enableCloud](#cloudsyncmanagerenablecloud). It uses a Promise asynchronous callback.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
cloudSyncManager.disableCloud(accountId).then(() => {
  console.info("disableCloud successfully");
}).catch((err: BusinessError) => {
  console.error(`disableCloud failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.disableCloud

disableCloud(accountId: string, callback: AsyncCallback&lt;void&gt;): void

Describes an asynchronous method to disable the end-cloud collaboration capability. It applies to the scenario where the end-cloud collaboration capability of applications under a specified account needs to be disabled, and can be Used Together with [enableCloud](#cloudsyncmanagerenablecloud). This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. Callback for the result after asynchronously disabling the end-cloud collaboration capability. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
cloudSyncManager.disableCloud(accountId, (err: BusinessError) => {
  if (err) {
    console.error(`disableCloud failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("disableCloud successfully");
  }
});
```

## Action

Enumeration for cleaning local cloud-related data.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name|  Value|  Description|
| ----- |  ---- |  ---- |
| RETAIN_DATA |  0 |  Clear the cloud identifier but retain the files cached locally.|
| CLEAR_DATA |  1 |  Clear the cloud identifier and the files cached locally.|

## cloudSyncManager.clean

clean(accountId: string, appActions: Record<string, Action>): Promise&lt;void&gt;

Asynchronously cleans local cloud-related data. This API is applicable to scenarios where local cloud-related data needs to be retained or deleted based on application configuration when an account logs out or application cloud data is cleaned up. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| appActions | Record<string, [Action](#action)> | Yes | The string type is the application package name to be cleaned, and [Action](#action) is the cleanup action type. |

**Return value**

| Type                 | Description            |
| --------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions).then(() => {
  console.info("clean successfully");
}).catch((err: BusinessError) => {
  console.error(`clean failed with error message: ${err.message}, error code: ${err.code}`);
});
```

## cloudSyncManager.clean

clean(accountId: string, appActions: Record<string, Action>, callback: AsyncCallback&lt;void&gt;): void

Asynchronously cleans local cloud-related data. This API is applicable to scenarios where local cloud-related data needs to be retained or deleted based on application configuration when an account logs out or application cloud data is cleaned up. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description|
| ---------- | ------ | ---- | ---- |
| accountId | string | Yes | Account ID. |
| appActions | Record<string, [Action](#action)> | Yes | The string type is the application package name to be cleaned, and [Action](#action) is the cleanup action type. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. Callback for the result after asynchronously cleaning local cloud-related data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID                    | Error Message       |
| ---------------------------- | ---------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let accountId: string = "testAccount";
let appActions: Record<string, cloudSyncManager.Action> = {
  'com.example.bundleName1': cloudSyncManager.Action.RETAIN_DATA,
  'com.example.bundleName2': cloudSyncManager.Action.CLEAR_DATA
};
cloudSyncManager.clean(accountId, appActions, (err: BusinessError) => {
  if (err) {
    console.error(`clean failed with error message: ${err.message}, error code: ${err.code}`);
  } else {
    console.info("clean successfully");
  }
});
```

## DowngradeDownload<sup>20+</sup>

Full download: provides the capability of downloading cloud data for applications.

It supports the full download of cloud application files.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

### constructor<sup>20+</sup>

constructor(bundleName: string)

A constructor used to create an instance of the **DowngradeDownload** class with a specified bundle name.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name    | Type  | Mandatory| Description      |
| ---------- | ------ | ---- | ---------- |
| bundleName | string | Yes  | Bundle name.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13900020 | Invalid argument. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.                                                                     |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.demo.a';
try {
  let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
} catch (e) {
  let error = e as BusinessError;
  console.error(`Failed to create downgrade manager object, error code: ${error.code}, message: ${error.message}`);
}
```

### getCloudFileInfo<sup>20+</sup>

getCloudFileInfo(): Promise&lt;CloudFileInfo&gt;

Obtains the size and count of files for applications requiring full download, including those stored only locally, only in the cloud, or both locally and in the cloud. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Return value**

  | Type                             | Description                    |
  | --------------------------------- | ------------------------ |
  | Promise&lt;[CloudFileInfo](js-apis-file-cloudsyncmanager.md#cloudfileinfo20)&gt; | Promise used to return the local and cloud file information.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13600001 | IPC error. Possible causes: 1.IPC failed or timed out. 2.Failed to load the service.                                                                                              |
| 13900010 | Try again.                                                                                                                                                                        |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.getCloudFileInfo().then((fileInfo: cloudSyncManager.CloudFileInfo) => {
  console.info("cloud file info: " + JSON.stringify(fileInfo));
}).catch((err: BusinessError) => {
  console.error(`Failed to get downgrade info, error message: ${err.message}, error code: ${err.code}`);
});
```

### startDownload<sup>20+</sup>

startDownload(callback: Callback&lt;DownloadProgress&gt;): Promise&lt;void&gt;

Starts full download of cloud files for a specified application. This API is applicable to scenarios where a cloud drive management application needs to centrally download cloud data of a specified application. This API uses a promise to return the result and returns the download progress through the callback parameter.

Repeated triggering of a full download task will throw an error (22400006).

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name  | Type                            | Mandatory| Description                                                                               |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------------------------------- |
| callback | Callback&lt;[DownloadProgress](js-apis-file-cloudsyncmanager.md#downloadprogress20)&gt; | Yes  | Callback function. Returns the download progress during the full download process. The parameter is DownloadProgress, and the return value is void. |

**Return value**

  | Type               | Description                     |
  | ------------------- | ------------------------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13600001 | IPC error. Possible causes: 1.IPC failed or timed out. 2.Failed to load the service.                                                                                              |
| 13900010 | Try again.                                                                                                                                                                        |
| 13900020 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types.                                                                     |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |
| 22400006 | The same task is already in progress.                                                                                                                                             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
let callback = (data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
  if (data.state == cloudSyncManager.DownloadState.COMPLETED) {
    console.info('Downgrade finished.');
  } else if (data.state == cloudSyncManager.DownloadState.STOPPED) {
    console.info(`Downgrade stopped, reason: ${data.stopReason}.`);
  }
};
downgradeMgr.startDownload(callback).then(() => {
  console.info("Downgrade started successfully.");
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});
```

### stopDownload<sup>20+</sup>

stopDownload(): Promise&lt;void&gt;

Stops the full download task triggered by [startDownload](#startdownload20). This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Return value**

  | Type               | Description                     |
  | ------------------- | ------------------------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                                                                                                         |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed, usually the result returned by VerifyAccessToken.                                                                                                 |
| 202      | Permission verification failed, application which is not a system application uses system API.                                                                                    |
| 13600001 | IPC error. Possible causes: 1.IPC failed or timed out. 2.Failed to load the service.                                                                                              |
| 22400005 | Inner error. Possible causes: 1.Failed to access the database or execute the SQL statement. 2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName: string = "com.demo.a";
let downgradeMgr = new cloudSyncManager.DowngradeDownload(bundleName);
downgradeMgr.startDownload((data: cloudSyncManager.DownloadProgress) => {
  console.info(`Downgrade progress: downloadedSize: ${data.downloadedSize}, totalSize: ${data.totalSize}`);
}).then(() => {
  console.info("Downgrade started successfully.");
  let needStop = true;
  if (needStop) {
    downgradeMgr.stopDownload().then(() => {
      console.info("Downgrade stopped successfully.");
    }).catch((err: BusinessError) => {
      console.error(`Failed to stop downgrade, error message: ${err.message}, error code: ${err.code}`);
    });
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to start downgrade, error message: ${err.message}, error code: ${err.code}`);
});
```

### startTransfer

startTransfer(targetUri: string, callback: Callback&lt;TransferProgress&gt;): void

Migrates files that have completed local download under the cloud drive directory to a specified directory. This API is suitable for scenarios where cloud drive files need to be exported to other local directories for management. During the process, the migration progress is reported through the callback. This API uses an asynchronous callback.

Repeated triggering of a migration task will throw an error (22400006).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------------------- | ---- | ----------------------------------------------------------------------------------- |
| targetUri | string | Yes | URI of the path used to store the migrated files. It must be prefixed with "file://docs/storage/Users/currentUser/". |
| callback | Callback&lt;[TransferProgress](#transferprogress)&gt; | Yes | Callback function. Returns the migration progress during the file migration process. The parameter is TransferProgress, and the return value is void. |

**Error codes**

For details about the following error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                                                                                                                                          |
| -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 201      | Permission verification failed.                                                                                                                                                   |
| 202      | The caller is not a system application.                                                                                                                                           |
| 13900001 | Operation not permitted. Possible causes:<br>1.The DowngradeDownload task is running.<br>2.The full data synchronization task is running.                                         |
| 13900002 | No such file or directory.                                                                                                                                                        |
| 13900010 | Try again.                                                                                                                                                                        |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified.<br>2.The length of the input uri does not meet the value range requirement.<br>3.The input uri does not belong to a File Manager public directory. |
| 22400006 | The same task is already in progress.                                                                                                                                             |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let targetPath: string = "file://docs/storage/Users/currentUser/Download/";
try {
    let downgradeMgr = new cloudSyncManager.DowngradeDownload("com.demo");
    downgradeMgr.startTransfer(targetPath, (data: cloudSyncManager.TransferProgress) => {
        console.info(`Transfer progress: successfulCount: ${data.successfulCount}, totalCount: ${data.totalCount}`);
    });
} catch (err) {
    let e = err as BusinessError;
    console.error(`transfer files failed with error message: ${e.message}, error code: ${e.code}`);
}
```

## TransferProgress

Progress information of the migration task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name            | Type                                        | Read-Only | Optional | Description                                                                          |
| --------------- | ------------------------------------------- | ---- | ---- | ----------------------------------------------------------------------------- |
| state           | [TransferState](#transferstate)             | No   | No   | State of the migration task.                                                              |
| successfulCount | number                                      | No   | No   | Number of migrated files. Value range: [0, INT32_MAX], unit: file. Returns -1 when the progress is abnormal.        |
| failedCount     | number                                      | No   | No   | Number of files that failed to migrate. Value range: [0, INT32_MAX], unit: file. Returns -1 when the progress is abnormal.      |
| totalCount      | number                                      | No   | No   | Total number of files to be migrated. Value range: [0, INT32_MAX], unit: file. Returns -1 when the progress is abnormal.        |
| transferredSize | number                                      | No   | No   | Size of migrated data. Value range: [0, INT64_MAX), unit: Byte. Returns INT64_MAX when the progress is abnormal. |
| totalSize       | number                                      | No   | No   | Total size of files to be migrated. Value range: [0, INT64_MAX), unit: Byte. Returns INT64_MAX when the progress is abnormal. |
| stopReason      | [TransferStopReason](#transferstopreason)   | No   | No   | Reason for the migration stop.                                                              |

## TransferState

Enumerates the states of a migration task.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name      | Value | Description       |
| --------- | ----- | ----------------- |
| RUNNING   | 0     | Migration in progress. |
| COMPLETED | 1     | Migration completed. |
| STOPPED   | 2     | Migration stopped. |

## TransferStopReason

Enumerates the reasons for migration stop.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name                | Value | Description                                                   |
| ------------------- | ----- | ------------------------------------------------------ |
| SWITCH_OFF          | 0     | The cloud service switch is turned off during the migration process.                                         |
| ACCOUNT_LOGOUT      | 1     | The account is logged out during the migration process.               |
| OTHER_REASON        | 2     | The migration stops due to other reasons during the migration process.                         |

## LocalFilePresentStatus<sup>23+</sup>

  Specifies a result object that contains the application bundle name and the status information about whether there are files that have not been uploaded to the cloud in the cloud storage space.

  **System API**: This is a system API.

  **System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager


  | Name| Type| Read-Only| Optional| Description|
  | ---- | ---- | ---- | ---- | ---- |
  | bundleName | string | No| No| Bundle name.|
  | isLocalFilePresent | boolean | No| No| Whether there are local files that have not been synchronized to the cloud in the cloud storage space of the application. The value **true** indicates that such file exists, and the value **false** indicates the opposite.|

## cloudSyncManager.getBundlesLocalFilePresentStatus<sup>23+</sup>

  getBundlesLocalFilePresentStatus(bundleNames: Array&lt;string&gt;): Promise&lt;Array&lt;LocalFilePresentStatus&gt;&gt;

  Obtains the existence status of local files for multiple applications and checks whether there are files that have not been uploaded to the cloud in the cloud storage space. This API uses a promise to return the result.

  **Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

  **System API**: This is a system API.

  **System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

  **Parameters**

  | Name| Type| Mandatory| Description|
  | ------ | ---- | ---- | ---- |
  | bundleNames | Array&lt;string&gt; | Yes| Array of application bundle names to be checked. Each element is the bundle name of an application.|

  **Return value**

  | Type| Description|
  | ---- | ---- |
  | Promise&lt;Array&lt;[LocalFilePresentStatus](#localfilepresentstatus23)&gt;&gt; | Promise used to return an array of objects. Each object in the array contains the bundle name of the application to be checked and the local file existence status.|

  **Error codes**

  For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

  | ID| Error Message|
  | -------- | -------- |
  | 201 | Permission verification failed. |
  | 202 | The caller is not a system application. |
  | 13600001 | IPC error. Possible causes: 1. IPC failed or timed out. 2. Failed to load the service. |
  | 13900010 | Try again. |
  | 13900020 | Invalid argument. Possible causes: 1. Mandatory parameters are left unspecified. 2. The length of the input parameter exceeds the upper limit. 3. The input parameter contains an invalid bundleName. |
  | 22400005 | Inner error. Possible causes: 1. Failed to access the database or execute the SQL statement. 2. System error, such as a null pointer, insufficient memory or a JS engine exception. |

  **Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getBundlesLocalFilePresentStatus(bundles).then((results: Array<cloudSyncManager.LocalFilePresentStatus>) => {
  results.forEach((item) => {
    console.info(`bundle: ${item.bundleName}, hasLocalUncloudedFiles: ${item.isLocalFilePresent}`);
  });
}).catch((err: BusinessError) => {
  console.error(`getBundlesLocalFilePresentStatus failed, code: ${err.code}, message: ${err.message}`);
});
```
## cloudSyncManager.getDowngradeDownloadTaskState

getDowngradeDownloadTaskState(bundleNames: Array&lt;string&gt;): Promise&lt;Array&lt;DownloadProgress&gt;&gt;

Queries the full download task state of applications connected to the cloud drive. This API uses a promise to return the result asynchronously.

Because the returned DownloadProgress object does not contain the bundle name, the caller must record the application package name when querying multiple applications in batches.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Required permissions**: ohos.permission.CLOUDFILE_SYNC_MANAGER

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ---- | ---- | ---- |
| bundleNames | Array&lt;string&gt; | Yes | Array of application package names to query. Each element is the package name string of an application. The maximum size of the package name array is 20. If the limit is exceeded, error code 13900020 is returned. |

**Return value**

| Type | Description |
| ---- | ---- |
| Promise&lt;Array&lt;[DownloadProgress](js-apis-file-cloudsyncmanager.md#downloadprogress20)&gt;&gt; | Promise object that returns the queried array of state information of the full download tasks. |

**Error codes**

For details about the following error codes, see [File Management Error Codes](errorcode-filemanagement.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes: 1. Mandatory parameters are left unspecified. 2. The length of the input parameter exceeds the upper limit. 3. The input parameter contains an invalid bundleName. |


**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getDowngradeDownloadTaskState(bundles).then((results: Array<cloudSyncManager.DownloadProgress>) => {
  results.forEach((item) => {
    console.info(`state: ${item.state}, downloadedSize: ${item.downloadedSize}, totalSize: ${item.totalSize}`);
    console.info(`successfulCount: ${item.successfulCount}, failedCount: ${item.failedCount}, totalCount: ${item.totalCount}`);
    if (item.state == cloudSyncManager.DownloadState.STOPPED) {
      console.info(`stopReason: ${item.stopReason}`);
    }
  });
}).catch((err: BusinessError) => {
  console.error(`getDowngradeDownloadTaskState failed, code: ${err.code}, message: ${err.message}`);
});
```

## DownloadState<sup>20+</sup>

Enumerates the states of a full download task.

**System capability**: SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

| Name      | Value  | Description                                    |
| --------- | --- | -------------------------------------- |
| MISSING   | 3   | The download task does not exist.<br>**Since Version**: 26.0.0<br>**Model Constraint**: This API can only be used under the Stage model.<br>**System API**: This API is a system API. |
