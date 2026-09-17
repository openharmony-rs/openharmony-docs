# registerAppGroupCallBack (System API)

## Modules to Import

```TypeScript
import { usageStatistics } from '@kit.BackgroundTasksKit';
```

## registerAppGroupCallBack

```TypeScript
function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>, callback: AsyncCallback<void>): void
```

Register appGroup change callback to service.

**Since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md)&gt; | Yes | callback of AppGroupCallbackInfo when the group of app changed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the registration is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [10000001](../errorcode-DeviceUsageStatistics.md#10000001-memory-operation-failure) | Memory operation failed. |
| [10000002](../errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../errorcode-DeviceUsageStatistics.md#10000003-system-service-operation-failure) | Failed to get system ability manager. |
| [10000004](../errorcode-DeviceUsageStatistics.md#10000004-ipc-failure) | Failed to access the device usage service. |
| [10100001](../errorcode-DeviceUsageStatistics.md#10100001-duplicate-application-group-operation) | Repeated operation on the application group. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

function onBundleGroupChanged(res: usageStatistics.AppGroupCallbackInfo) {
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack RegisterGroupCallBack callback success.');
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appOldGroup is : ' + res.appOldGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appNewGroup is : ' + res.appNewGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result changeReason is : ' + res.changeReason);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result userId is : ' + res.userId);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result bundleName is : ' + res.bundleName);
};
usageStatistics.registerAppGroupCallBack(onBundleGroupChanged).then( () => {
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack promise succeeded.');
}).catch((err: BusinessError) => {
  console.error('BUNDLE_ACTIVE registerAppGroupCallBack promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { usageStatistics } from '@kit.BackgroundTasksKit';

function onBundleGroupChanged(res: usageStatistics.AppGroupCallbackInfo) {
  console.info('BUNDLE_ACTIVE onBundleGroupChanged RegisterGroupCallBack callback success.');
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appOldGroup is : ' + res.appOldGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result appNewGroup is : ' + res.appNewGroup);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result changeReason is : ' + res.changeReason);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result userId is : ' + res.userId);
  console.info('BUNDLE_ACTIVE registerAppGroupCallBack result bundleName is : ' + res.bundleName);
};
usageStatistics.registerAppGroupCallBack(onBundleGroupChanged, (err: BusinessError) => {
  if(err) {
    console.error('BUNDLE_ACTIVE registerAppGroupCallBack callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('BUNDLE_ACTIVE registerAppGroupCallBack callback success.');
  }
});
```


## registerAppGroupCallBack

```TypeScript
function registerAppGroupCallBack(groupCallback: Callback<AppGroupCallbackInfo>): Promise<void>
```

Register appGroup change callback to service.

**Since:** 9

**Required permissions:** ohos.permission.BUNDLE_ACTIVE_INFO

**System capability:** SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| groupCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AppGroupCallbackInfo](arkts-backgroundtasks-usagestatistics-appgroupcallbackinfo-i-sys.md)&gt; | Yes | callback of AppGroupCallbackInfo when the group of app changed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by registerAppGroupCallBack. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameters types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [10000001](../errorcode-DeviceUsageStatistics.md#10000001-memory-operation-failure) | Memory operation failed. |
| [10000002](../errorcode-DeviceUsageStatistics.md#10000002-ipc-parcel-write-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters;<br> 2. Failed to apply for memory. |
| [10000003](../errorcode-DeviceUsageStatistics.md#10000003-system-service-operation-failure) | Failed to get system ability manager. |
| [10000004](../errorcode-DeviceUsageStatistics.md#10000004-ipc-failure) | Failed to access the device usage service. |
| [10100001](../errorcode-DeviceUsageStatistics.md#10100001-duplicate-application-group-operation) | Repeated operation on the application group. |

**Examples**

See [registerAppGroupCallBack](#registerappgroupcallback)
