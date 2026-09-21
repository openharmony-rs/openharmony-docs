# queryAppGroup (System API)

## Modules to Import

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## queryAppGroup

```TypeScript
function queryAppGroup(callback: AsyncCallback<number>): void
```

Queries the app group of the calling application.

The priority defined in a priority group restricts the resource usage of an application, for example, restricting the running of background tasks.

**Since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**, and data is the app group of the calling application. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [10000001](../errorcode-DeviceUsageStatistics.md#10000001-memory-operation-failure) | Memory operation failed. |
| [10000002](../errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../errorcode-DeviceUsageStatistics.md#10000003-system-service-operation-failure) | Failed to get system ability manager. |
| [10000004](../errorcode-DeviceUsageStatistics.md#10000004-ipc-failure) | Failed to access the device usage service. |
| [10000005](../errorcode-DeviceUsageStatistics.md#10000005-application-not-installed) | Application is not installed. |
| [10000006](../errorcode-DeviceUsageStatistics.md#10000006-failed-to-obtain-application-information) | Failed to get the application information. |
| [10100002](../errorcode-DeviceUsageStatistics.md#10100002-failed-to-obtain-application-group-information) | Failed to get the application group information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.queryAppGroup((err: BusinessError, res: number) => {
  if(err) {
    console.error('BUNDLE_ACTIVE queryAppGroup callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('BUNDLE_ACTIVE queryAppGroup callback succeeded. result: ' + JSON.stringify(res));
  }
});
```


<a id="queryappgroup-1"></a>

## queryAppGroup

```TypeScript
function queryAppGroup(): Promise<number>
```

Queries the app group of the calling application.

The priority defined in a priority group restricts the resource usage of an application, for example, restricting the running of background tasks.

**Since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | the promise returned by queryAppGroup. Returns the app group of the calling application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [10000001](../errorcode-DeviceUsageStatistics.md#10000001-memory-operation-failure) | Memory operation failed. |
| [10000002](../errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../errorcode-DeviceUsageStatistics.md#10000003-system-service-operation-failure) | Failed to get system ability manager. |
| [10000004](../errorcode-DeviceUsageStatistics.md#10000004-ipc-failure) | Failed to access the device usage service. |
| [10000005](../errorcode-DeviceUsageStatistics.md#10000005-application-not-installed) | Application is not installed. |
| [10000006](../errorcode-DeviceUsageStatistics.md#10000006-failed-to-obtain-application-information) | Failed to get the application information. |
| [10100002](../errorcode-DeviceUsageStatistics.md#10100002-failed-to-obtain-application-group-information) | Failed to get the application group information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

usageStatistics.queryAppGroup().then((res: number) => {
  console.info('BUNDLE_ACTIVE queryAppGroup promise succeeded. result: ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE queryAppGroup promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```


<a id="queryappgroup-2"></a>

## queryAppGroup

```TypeScript
function queryAppGroup(bundleName: string, callback: AsyncCallback<number>): void
```

Queries the usage priority group by bundleName.

The priority defined in a priority group restricts the resource usage of an application, for example, restricting the running of background tasks.

**Since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | name of the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the query is successful, **err** is **undefined**, and data is the usage priority group of the calling application. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [10000001](../errorcode-DeviceUsageStatistics.md#10000001-memory-operation-failure) | Memory operation failed. |
| [10000002](../errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../errorcode-DeviceUsageStatistics.md#10000003-system-service-operation-failure) | Failed to get system ability manager. |
| [10000004](../errorcode-DeviceUsageStatistics.md#10000004-ipc-failure) | Failed to access the device usage service. |
| [10000005](../errorcode-DeviceUsageStatistics.md#10000005-application-not-installed) | Application is not installed. |
| [10000006](../errorcode-DeviceUsageStatistics.md#10000006-failed-to-obtain-application-information) | Failed to get the application information. |
| [10100002](../errorcode-DeviceUsageStatistics.md#10100002-failed-to-obtain-application-group-information) | Failed to get the application group information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

let bundleName: string = "com.ohos.camera";
usageStatistics.queryAppGroup(bundleName, (err: BusinessError, res: number) => {
  if(err) {
    console.error('BUNDLE_ACTIVE queryAppGroup callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('BUNDLE_ACTIVE queryAppGroup callback succeeded. result: ' + JSON.stringify(res));
  }
});
```


<a id="queryappgroup-3"></a>

## queryAppGroup

```TypeScript
function queryAppGroup(bundleName: string): Promise<number>
```

Queries the usage priority group by bundleName.

The priority defined in a priority group restricts the resource usage of an application, for example, restricting the running of background tasks.

**Since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the calling application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [10000001](../errorcode-DeviceUsageStatistics.md#10000001-memory-operation-failure) | Memory operation failed. |
| [10000002](../errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../errorcode-DeviceUsageStatistics.md#10000003-system-service-operation-failure) | Failed to get system ability manager. |
| [10000004](../errorcode-DeviceUsageStatistics.md#10000004-ipc-failure) | Failed to access the device usage service. |
| [10000005](../errorcode-DeviceUsageStatistics.md#10000005-application-not-installed) | Application is not installed. |
| [10000006](../errorcode-DeviceUsageStatistics.md#10000006-failed-to-obtain-application-information) | Failed to get the application information. |
| [10100002](../errorcode-DeviceUsageStatistics.md#10100002-failed-to-obtain-application-group-information) | Failed to get the application group information. |

**Examples**

```TypeScript
// Promise mode when bundleName is specified
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

let bundleName: string = "com.ohos.camera";
usageStatistics.queryAppGroup(bundleName).then((res: number) => {
  console.info('BUNDLE_ACTIVE queryAppGroup promise succeeded. result: ' + JSON.stringify(res));
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE queryAppGroup promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```
