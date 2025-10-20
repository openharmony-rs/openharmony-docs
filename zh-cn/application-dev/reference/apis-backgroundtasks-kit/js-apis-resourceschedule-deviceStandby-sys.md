# @ohos.resourceschedule.deviceStandby (设备待机模块)(系统接口)
<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @geng_wd-->
<!--Designer: @geng_wd-->
<!--Tester: @wzzqishi-->
<!--Adviser: @Brilliantry_Rui-->

当设备长时间未被使用或通过按键，可以使设备进入待机模式。待机模式不影响应用使用，还可以延长电池续航时间。通过本模块接口，可查询设备或应用是否为待机模式，以及为应用申请或取消待机资源管控。

>  **说明**:
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口为系统接口。

## 导入模块

```ts
import { deviceStandby } from '@kit.BackgroundTasksKit';
```

## deviceStandby.getExemptedApps

getExemptedApps(resourceTypes: number, callback: AsyncCallback<Array&lt;ExemptedAppInfo&gt;>): void

获取进入待机模式的应用名单，使用Callback异步回调。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby

**需要权限:** ohos.permission.DEVICE_STANDBY_EXEMPTION


**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| ResourceTypes|number | 是    | 资源类型，类型具体说明请参考[ResourceType](#resourcetype)。 |
| callback | AsyncCallback<Array&lt;[ExemptedAppInfo](#exemptedappinfo)&gt;> | 是    |豁免应用信息。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[backgroundTaskManager错误码](errorcode-backgroundTaskMgr.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**示例**：

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

获取进入待机模式的应用名单，使用Promise异步回调。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby

**需要权限:** ohos.permission.DEVICE_STANDBY_EXEMPTION


**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| ResourceTypes|number | 是    |资源类型，类型具体说明请参考[ResourceType](#resourcetype)。|

**返回值**：

| 类型                    | 说明                                       |
| --------------------- | ---------------------------------------- |
| Promise<Array&lt;[ExemptedAppInfo](#exemptedappinfo)&gt;> | 豁免应用信息。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[backgroundTaskManager错误码](errorcode-backgroundTaskMgr.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**示例**：

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

应用订阅申请豁免，使应用临时不进入待机管控。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby

**需要权限:** ohos.permission.DEVICE_STANDBY_EXEMPTION


**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| request |[ResourceRequest](#resourcerequest)| 是    | 资源请求。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[backgroundTaskManager错误码](errorcode-backgroundTaskMgr.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**示例**：

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

取消应用订阅申请豁免。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby

**需要权限:** ohos.permission.DEVICE_STANDBY_EXEMPTION


**参数**：

| 参数名      | 类型                   | 必填   | 说明                             |
| -------- | -------------------- | ---- | ------------------------------ |
| request |[ResourceRequest](#resourcerequest)| 是    | 资源请求 。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[backgroundTaskManager错误码](errorcode-backgroundTaskMgr.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 201  | Permission denied. |
| 202 | Not System App. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| 9800001 | Memory operation failed. |
| 9800002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters. |
| 9800003 | Failed to complete inner transaction. |
| 9800004 | Failed to get device standby service. Possible cause: A necessary system service is not ready. |
| 18700001 | Caller information verification failed. |

**示例**：

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

非待机应用资源枚举。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby


|名称   |值   |说明|
| ------------ | ------------ |--------------|
|NETWORK    |1   |网络访问资源。|
|RUNNING_LOCK    |2   |cpu-runninglock资源。|
|TIMER     |4   | timer任务资源。|
|WORK_SCHEDULER     |8   | work任务资源。|
|AUTO_SYNC      |16   | 自动同步的资源。 |
|PUSH     |32   | pushkit资源。|
|FREEZE       |64   | 冻结应用资源。|

## ExemptedAppInfo

豁免应用信息，未进入待机管控的应用信息。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby


|名称  |类型   | 只读   | 可选   |说明   |
| ------------ | ------------ |------------ |------------ | ------------ |
|resourceTypes   | number  | 否   | 否   |资源类型，类型具体说明请参考[ResourceType](#resourcetype)。   |
|name   |string   | 否   | 否   |  应用名。  |
|duration   | number  | 否   | 否   | 豁免时长。 |

## ResourceRequest

待机资源请求体。

**系统能力:** SystemCapability.ResourceSchedule.DeviceStandby


|名称   |类型   | 只读  | 可选   |说明   |
| ------------ | ------------ |------------ |------------| ------------ |
|resourceTypes   | number  | 否 | 否   |资源类型，类型具体说明请参考[ResourceType](#resourcetype)。   |
|uid   | number  | 否  | 否   |应用uid。   |
|name   |string   | 否 | 否    | 应用名称。  |
|duration   | number    | 否 | 否    | 豁免时长。 |
|reason   |string   | 否  | 否   |  申请原因。  |