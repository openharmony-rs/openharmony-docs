# getExemptedApps (System API)

## Modules to Import

```TypeScript
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## getExemptedApps

```TypeScript
function getExemptedApps(resourceTypes: number, callback: AsyncCallback<Array<ExemptedAppInfo>>): void
```

Returns the information about the specified exempted application.

**Since:** 10

**Required permissions:** ohos.permission.DEVICE_STANDBY_EXEMPTION

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceTypes | number | Yes | the combination of [ResourceType](arkts-backgroundtasks-devicestandby-resourcetype-e-sys.md) values. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ExemptedAppInfo](arkts-backgroundtasks-devicestandby-exemptedappinfo-i-sys.md)&gt;&gt; | Yes | the callback of getExemptedApps. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800002](../errorcode-backgroundTaskMgr.md#9800002-parcel-readwrite-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| [9800003](../errorcode-backgroundTaskMgr.md#9800003-ipc-failure) | Failed to complete inner transaction. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| [18700001](../errorcode-backgroundTaskMgr.md#18700001-caller-information-verification-failure-for-an-energy-resource-request) | Caller information verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { deviceStandby } from '@kit.BackgroundTasksKit';

let resourceTypes: deviceStandby.ResourceType  = deviceStandby.ResourceType.TIMER | deviceStandby.ResourceType.NETWORK;
deviceStandby.getExemptedApps(resourceTypes, (err: BusinessError, res: Array<deviceStandby.ExemptedAppInfo>) => {
  if (err) {
    console.error('DEVICE_STANDBY getExemptedApps callback failed. code is: ' + err.code + ',message is: ' + err.message);
  } else {
    console.info('DEVICE_STANDBY getExemptedApps callback success.');
    for (let i = 0; i < res.length; i++) {
      console.info('DEVICE_STANDBY getExemptedApps callback result ' + JSON.stringify(res[i]));
    }
  }
});
```


<a id="getexemptedapps-1"></a>

## getExemptedApps

```TypeScript
function getExemptedApps(resourceTypes: number): Promise<Array<ExemptedAppInfo>>
```

Returns the information about the specified exempted application.

**Since:** 10

**Required permissions:** ohos.permission.DEVICE_STANDBY_EXEMPTION

**System capability:** SystemCapability.ResourceSchedule.DeviceStandby

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceTypes | number | Yes | the combination of [ResourceType](arkts-backgroundtasks-devicestandby-resourcetype-e-sys.md) values. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ExemptedAppInfo](arkts-backgroundtasks-devicestandby-exemptedappinfo-i-sys.md)&gt;&gt; | the promise returned by getExemptedApps. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [9800001](../errorcode-backgroundTaskMgr.md#9800001-memory-operation-failure) | Memory operation failed. |
| [9800002](../errorcode-backgroundTaskMgr.md#9800002-parcel-readwrite-operation-failure) | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| [9800003](../errorcode-backgroundTaskMgr.md#9800003-ipc-failure) | Failed to complete inner transaction. |
| [9800004](../errorcode-backgroundTaskMgr.md#9800004-system-service-failure) | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| [18700001](../errorcode-backgroundTaskMgr.md#18700001-caller-information-verification-failure-for-an-energy-resource-request) | Caller information verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { deviceStandby } from '@kit.BackgroundTasksKit';

let resourceTypes: deviceStandby.ResourceType = deviceStandby.ResourceType.TIMER | deviceStandby.ResourceType.NETWORK;
deviceStandby.getExemptedApps(resourceTypes).then( (res: Array<deviceStandby.ExemptedAppInfo>) => {
  console.info('DEVICE_STANDBY getExemptedApps promise success.');
  for (let i = 0; i < res.length; i++) {
    console.info('DEVICE_STANDBY getExemptedApps promise result ' + JSON.stringify(res[i]));
  }
}).catch( (err: BusinessError) => {
  console.error('DEVICE_STANDBY getExemptedApps promise failed. code is: ' + err.code + ',message is: ' + err.message);
});
```
