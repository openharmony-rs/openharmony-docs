# @ohos.resourceschedule.deviceStandby (Device Standby) (System API)
<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @geng_wd-->
<!--Designer: @geng_wd-->
<!--Tester: @wzzqishi-->
<!--Adviser: @Brilliantry_Rui-->

A device enters standby mode if it is unused for a long period of time or after the Power button is pressed. The standby mode prolongs the battery life without affecting the use of applications. The **deviceStandby** module provides APIs for you to check whether a device is in standby mode and request or cancel standby resource control for an application.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## deviceStandby.getExemptedApps

getExemptedApps(resourceTypes: number, callback: AsyncCallback<Array&lt;ExemptedAppInfo&gt;>): void

Obtains the list of applications that can still use resources of the specified types when the device is in standby mode. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby

**Required permissions**: ohos.permission.DEVICE_STANDBY_EXEMPTION


**Parameters**

| Name     | Type                  | Mandatory  | Description                            |
| -------- | -------------------- | ---- | ------------------------------ |
| ResourceTypes|number | Yes   | Resource types. For details, see [ResourceType](#resourcetype).|
| callback | AsyncCallback<Array&lt;[ExemptedAppInfo](#exemptedappinfo)&gt;> | Yes   |Callback used to return the exempted application information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**Example**

```ts
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

## deviceStandby.getExemptedApps

getExemptedApps(resourceTypes: number): Promise<Array&lt;ExemptedAppInfo&gt;>

Obtains the list of applications that can still use resources of the specified types when the device is in standby mode. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby

**Required permissions**: ohos.permission.DEVICE_STANDBY_EXEMPTION


**Parameters**

| Name     | Type                  | Mandatory  | Description                            |
| -------- | -------------------- | ---- | ------------------------------ |
| ResourceTypes|number | Yes   |Resource types. For details, see [ResourceType](#resourcetype).|

**Return value**

| Type                   | Description                                      |
| --------------------- | ---------------------------------------- |
| Promise<Array&lt;[ExemptedAppInfo](#exemptedappinfo)&gt;> | Promise used to return the exempted application information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**Example**

```ts
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

## deviceStandby.requestExemptionResource

requestExemptionResource(request: ResourceRequest): void

Requests exemption, so that the application can use restricted resources when the device is in standby mode.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby

**Required permissions**: ohos.permission.DEVICE_STANDBY_EXEMPTION


**Parameters**

| Name     | Type                  | Mandatory  | Description                            |
| -------- | -------------------- | ---- | ------------------------------ |
| request |[ResourceRequest](#resourcerequest)| Yes   | Request body.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**Example**

```ts
import { deviceStandby } from '@kit.BackgroundTasksKit';

let resRequest: deviceStandby.ResourceRequest = {
  resourceTypes: deviceStandby.ResourceType.TIMER,
  uid:10003,
  name:"com.example.app",
  duration:10,
  reason:"apply",
};
deviceStandby.requestExemptionResource(resRequest);
```

## deviceStandby.releaseExemptionResource

releaseExemptionResource(request: ResourceRequest): void

Cancels exemption for the application.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby

**Required permissions**: ohos.permission.DEVICE_STANDBY_EXEMPTION


**Parameters**

| Name     | Type                  | Mandatory  | Description                            |
| -------- | -------------------- | ---- | ------------------------------ |
| request |[ResourceRequest](#resourcerequest)| Yes   | Request body.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [backgroundTaskManager Error Codes](errorcode-backgroundTaskMgr.md).

| ID | Error Message            |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**Example**

```ts
import { deviceStandby } from '@kit.BackgroundTasksKit';

let resRequest: deviceStandby.ResourceRequest = {
  resourceTypes: deviceStandby.ResourceType.TIMER,
  uid:10003,
  name:"com.demo.app",
  duration:10,
  reason:"unapply",
};
deviceStandby.releaseExemptionResource(resRequest);
```

## ResourceType

Enumerates the types of resources that can be used by exempted applications.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby


|Name  |Value  |Description|
| ------------ | ------------ |--------------|
|NETWORK    |1   |Network access resource.|
|RUNNING_LOCK    |2   |CPU running lock resource.|
|TIMER     |4   | Timer task resource.|
|WORK_SCHEDULER     |8   | Work task resource.|
|AUTO_SYNC      |16   | Automatic synchronization resource.|
|PUSH     |32   | Push kit resource.|
|FREEZE       |64   | Freezing application resource.|

## ExemptedAppInfo

Defines the information about an exempted application.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby


|Name |Type  | Read-Only  | Optional  |Description  |
| ------------ | ------------ |------------ |------------ | ------------ |
|resourceTypes   | number  | No  | No  |Resource types. For details, see [ResourceType](#resourcetype).  |
|name   |string   | No  | No  |  Name of the application. |
|duration   | number  | No  | No  | Exemption duration.|

## ResourceRequest

Defines the message used to request to be an exempted application.

**System capability**: SystemCapability.ResourceSchedule.DeviceStandby


|Name  |Type  | Read-Only | Optional  |Description  |
| ------------ | ------------ |------------ |------------| ------------ |
|resourceTypes   | number  | No| No  |Resource types. For details, see [ResourceType](#resourcetype).  |
|uid   | number  | No | No  |UID of the application.  |
|name   |string   | No| No   | Name of the application. |
|duration   | number    | No| No   | Exemption duration.|
|reason   |string   | No | No  |  Reason for the request. |
