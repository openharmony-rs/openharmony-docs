# @ohos.resourceschedule.workScheduler (延迟任务调度)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @fenglili18-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供延迟任务注册、取消、查询的能力。在开发过程中，对于实时性要求不高的任务，可以调用本模块接口注册延迟任务，在系统空闲时根据性能、功耗、热等情况进行调度执行。

>  **说明：**
>
>  本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { workScheduler } from '@kit.BackgroundTasksKit';
```

## workScheduler.startWork

startWork(work: WorkInfo): void

申请延迟任务。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名  | 类型                    | 必填   | 说明             |
| ---- | --------------------- | ---- | -------------- |
| work | [WorkInfo](#workinfo) | 是    | 要添加到执行队列的延迟任务。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |
| 9700005 | Calling startWork failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  
  let workInfo: workScheduler.WorkInfo = {
      workId: 1,
      batteryStatus:workScheduler.BatteryStatus.BATTERY_STATUS_LOW,
      isRepeat: false,
      isPersisted: true,
      bundleName: "com.example.myapplication",
      abilityName: "MyExtension",
      parameters: {
          mykey0: 1,
          mykey1: "string value",
          mykey2: true,
          mykey3: 1.5
      }
  }
  try{
    workScheduler.startWork(workInfo);
    console.info('workschedulerLog startWork success');
  } catch (error) {
    console.error(`workschedulerLog startwork failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
  }
```

## workScheduler.stopWork

stopWork(work: WorkInfo, needCancel?: boolean): void

取消延迟任务。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名        | 类型                    | 必填   | 说明         |
| ---------- | --------------------- | ---- | ---------- |
| work       | [WorkInfo](#workinfo) | 是    | 要停止或移除的延迟任务。 |
| needCancel | boolean               | 否    | 是否需要移除任务。<br>true表示停止并移除，false表示只停止不移除。默认为false。|

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  let workInfo: workScheduler.WorkInfo = {
      workId: 1,
      batteryStatus:workScheduler.BatteryStatus.BATTERY_STATUS_LOW,
      isRepeat: false,
      isPersisted: true,
      bundleName: "com.example.myapplication",
      abilityName: "MyExtension",
      parameters: {
          mykey0: 1,
          mykey1: "string value",
          mykey2: true,
          mykey3: 1.5
      }
     }
  try{
    workScheduler.stopWork(workInfo, false);
    console.info('workschedulerLog stopWork success');
  } catch (error) {
    console.error(`workschedulerLog stopWork failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
  }
```

## workScheduler.getWorkStatus

getWorkStatus(workId: number, callback : AsyncCallback\<WorkInfo>): void

通过workId获取延迟任务，使用Callback异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名      | 类型                                    | 必填   | 说明                                       |
| -------- | ------------------------------------- | ---- | ---------------------------------------- |
| workId   | number                                | 是    | 延迟任务Id。                                 |
| callback | AsyncCallback\<[WorkInfo](#workinfo)> | 是    | 回调函数。如果workId有效，则返回从WorkSchedulerService获取的任务，否则抛出异常。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  workScheduler.getWorkStatus(50, (error: BusinessError, res: workScheduler.WorkInfo) => {
    if (error) {
      console.error(`workschedulerLog getWorkStatus failed. code is ${error.code} message is ${error.message}`);
    } else {
      console.info(`workschedulerLog getWorkStatus success, ${JSON.stringify(res)}`);
    }
  });
```

## workScheduler.getWorkStatus

getWorkStatus(workId: number): Promise\<WorkInfo>

通过workId获取延迟任务，使用Promise异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名    | 类型     | 必填   | 说明       |
| ------ | ------ | ---- | -------- |
| workId | number | 是    | 延迟任务Id。 |

**返回值**：

| 类型                              | 说明                                       |
| ------------------------------- | ---------------------------------------- |
| Promise\<[WorkInfo](#workinfo)> | Promise对象，如果workId有效，则返回从WorkSchedulerService获取的任务，否则抛出异常。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  workScheduler.getWorkStatus(50).then((res: workScheduler.WorkInfo) => {
    console.info(`workschedulerLog getWorkStatus success, ${JSON.stringify(res)}`);
  }).catch((error: BusinessError) => {
    console.error(`workschedulerLog getWorkStatus failed. code is ${error.code} message is ${error.message}`);
  })
```

## workScheduler.obtainAllWorks<sup>(deprecated)<sup>

obtainAllWorks(callback : AsyncCallback\<void>) : Array\<WorkInfo>
> 从API version 10开始不再维护，建议使用[workScheduler.obtainAllWorks<sup>10+<sup>](#workschedulerobtainallworks10)替代

获取当前应用所有的延迟任务，使用Callback异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名      | 类型                   | 必填   | 说明                              |
| -------- | -------------------- | ---- | ------------------------------- |
| callback |  AsyncCallback\<void> | 是    | 回调函数，获取成功时，err为undefined，否则为错误对象。 |

**返回值**：

| 类型                              | 说明                                       |
| ------------------------------- | ---------------------------------------- |
| Array\<[WorkInfo](#workinfo)> | 延迟任务列表，如果已添加延迟任务到执行队列，则返回当前应用所有的延迟任务列表；否则返回空列表。|
  
**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |

## workScheduler.obtainAllWorks<sup>10+<sup>

obtainAllWorks(callback : AsyncCallback&lt;Array&lt;WorkInfo&gt;&gt;): void

获取当前应用所有的延迟任务，使用Callback异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名      | 类型                   | 必填   | 说明                              |
| -------- | -------------------- | ---- | ------------------------------- |
| callback |  AsyncCallback&lt;Array&lt;WorkInfo&gt;&gt; | 是    | 回调函数，获取成功时，err为undefined，否则为错误对象。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  workScheduler.obtainAllWorks((error: BusinessError, res: Array<workScheduler.WorkInfo>) =>{
    if (error) {
      console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
    } else {
      console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
    }
  });
```

## workScheduler.obtainAllWorks

obtainAllWorks(): Promise\<Array\<WorkInfo>>

获取当前应用所有的延迟任务，使用Promise异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**返回值**：

| 类型                                     | 说明                             |
| -------------------------------------- | ------------------------------ |
| Promise<Array\<[WorkInfo](#workinfo)>> | Promise对象，返回当前应用所有的延迟任务。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  workScheduler.obtainAllWorks().then((res: Array<workScheduler.WorkInfo>) => {
    console.info(`workschedulerLog obtainAllWorks success, data is: ${JSON.stringify(res)}`);
  }).catch((error: BusinessError) => {
    console.error(`workschedulerLog obtainAllWorks failed. code is ${error.code} message is ${error.message}`);
  })
```

## workScheduler.stopAndClearWorks

stopAndClearWorks(): void

停止和取消当前应用所有的延迟任务。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  try{
    workScheduler.stopAndClearWorks();
    console.info(`workschedulerLog stopAndClearWorks success`);
  } catch (error) {
    console.error(`workschedulerLog stopAndClearWorks failed. code is ${(error as BusinessError).code} message is ${(error as BusinessError).message}`);
  }
```

## workScheduler.isLastWorkTimeOut<sup>(deprecated)<sup>

isLastWorkTimeOut(workId: number, callback : AsyncCallback\<void>): boolean

> 从API version 10开始不再维护，建议使用[workScheduler.isLastWorkTimeOut<sup>10+<sup>](#workschedulerislastworktimeout10)替代

检查延迟任务的最后一次执行是否超时，使用Callback异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名      | 类型                   | 必填   | 说明                                       |
| -------- | -------------------- | ---- | ---------------------------------------- |
| workId   | number               | 是    | 指定延迟任务的Id。                                 |
| callback | AsyncCallback\<void> | 是    | 回调函数。 |

**返回值**：

| 类型                              | 说明                                       |
| ------------------------------- | ---------------------------------------- |
|boolean| 检查延迟任务最后一次执行是否超时，如果workId有效，则返回从WorkSchedulerService获取的任务最后一次执行是否超时；否则，抛出异常。true，对应workId延迟任务最后一次执行超时，false，对应workId延迟任务最后一次执行未超时。|
  
**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |

## workScheduler.isLastWorkTimeOut<sup>10+<sup>

isLastWorkTimeOut(workId: number, callback : AsyncCallback\<boolean>): void

检查延迟任务的最后一次执行是否超时，使用Callback异步回调。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名      | 类型                   | 必填   | 说明                                       |
| -------- | -------------------- | ---- | ---------------------------------------- |
| workId   | number               | 是    | 指定延迟任务的Id。                                 |
| callback | AsyncCallback\<boolean> | 是    | 回调函数。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  workScheduler.isLastWorkTimeOut(500, (error: BusinessError, res: boolean) =>{
    if (error) {
      console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
    } else {
      console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
    }
  });
```

## workScheduler.isLastWorkTimeOut

isLastWorkTimeOut(workId: number): Promise\<boolean>

检查延迟任务的最后一次执行是否超时，使用Promise形式返回。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名    | 类型     | 必填   | 说明       |
| ------ | ------ | ---- | -------- |
| workId | number | 是    | 指定延迟任务的Id。 |

**返回值**：

| 类型                | 说明                                       |
| ----------------- | ---------------------------------------- |
| Promise\<boolean> | Promise对象。返回true表示指定任务的最后一次执行超时，false表示未超时。 |

**错误码**：

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[workScheduler错误码](errorcode-workScheduler.md)。

| 错误码ID  | 错误信息             |
| ---- | --------------------- |
| 401 | Parameter error. Possible causes: Parameter verification failed. |
| 9700001 | Memory operation failed. |
| 9700002 | Failed to write data into parcel. Possible reasons: 1. Invalid parameters; 2. Failed to apply for memory. |
| 9700003 | System service operation failed. |
| 9700004 | Check on workInfo failed. |

**示例**：

```ts
  import { BusinessError } from '@kit.BasicServicesKit';

  workScheduler.isLastWorkTimeOut(500)
    .then((res: boolean) => {
      console.info(`workschedulerLog isLastWorkTimeOut success, data is: ${res}`);
    })
    .catch((error: BusinessError) =>  {
      console.error(`workschedulerLog isLastWorkTimeOut failed. code is ${error.code} message is ${error.message}`);
    });
```

## WorkInfo

延迟任务的具体信息。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称             | 类型                                | 必填   | 说明               |
| --------------- | --------------------------------- | ---- | ---------------- |
| workId          | number                            | 是    | 延迟任务ID。          |
| bundleName      | string                            | 是    | 延迟任务所在应用的包名。           |
| abilityName     | string                            | 是    | 包内ability名称。 |
| networkType     | [NetworkType](#networktype)       | 否    | 网络类型。             |
| isCharging      | boolean                           | 否    | 是否充电，默认为false。<br>- true表示充电触发延迟回调。<br>- false表示不充电触发延迟回调。|
| chargerType     | [ChargingType](#chargingtype)     | 否    | 充电类型。             |
| batteryLevel    | number                            | 否    | 电量。              |
| batteryStatus   | [BatteryStatus](#batterystatus)   | 否    | 电池状态。             |
| storageRequest  | [StorageRequest](#storagerequest) | 否    | 存储状态。             |
| isRepeat        | boolean                           | 否    | 是否循环任务，默认为false。<br>- true表示循环任务。 <br>- false表示非循环任务。 |
| repeatCycleTime | number                            | 否    | 循环间隔，单位为毫秒。             |
| repeatCount     | number                            | 否    | 循环次数。             |
| isPersisted     | boolean                           | 否    | 注册的延迟任务是否可保存在系统中，默认为false。<br>- true表示可保存，即系统重启后，任务可恢复。<br>- false表示不可保存。|
| isDeepIdle      | boolean                           | 否    | 是否要求设备进入空闲状态，默认为false。<br>- true表示需要。<br>- false表示不需要。   |
| idleWaitTime    | number                            | 否    | 空闲等待时间，单位为毫秒。           |
| parameters      | Record<string, number \| string \| boolean>  | 否    | 携带参数信息。 |

## NetworkType

触发延迟回调的网络类型。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称                     | 值  | 说明                      |
| ---------------------- | ---- | ----------------------- |
| NETWORK_TYPE_ANY       | 0    | 表示这个触发条件是任何类型的网络连接。     |
| NETWORK_TYPE_MOBILE    | 1    | 表示这个触发条件是Mobile网络连接。    |
| NETWORK_TYPE_WIFI      | 2    | 表示这个触发条件是Wifi类型的网络连接。   |
| NETWORK_TYPE_BLUETOOTH | 3    | 表示这个触发条件是Bluetooth网络连接。 |
| NETWORK_TYPE_WIFI_P2P  | 4    | 表示这个触发条件是Wifi P2P网络连接。  |
| NETWORK_TYPE_ETHERNET  | 5    | 表示这个触发条件是有线网络连接。        |

## ChargingType

触发延迟回调的充电类型。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称                        | 值  | 说明                   |
| ------------------------- | ---- | -------------------- |
| CHARGING_PLUGGED_ANY      | 0    | 表示这个触发条件是任何类型的充电器连接。 |
| CHARGING_PLUGGED_AC       | 1    | 表示这个触发条件是直流充电器连接。    |
| CHARGING_PLUGGED_USB      | 2    | 表示这个触发条件是USB充连接。     |
| CHARGING_PLUGGED_WIRELESS | 3    | 表示这个触发条件是无线充电器连接。    |

## BatteryStatus

触发延迟回调的电池状态。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称                         | 值  | 说明                         |
| -------------------------- | ---- | -------------------------- |
| BATTERY_STATUS_LOW         | 0    | 表示这个触发条件是低电告警。             |
| BATTERY_STATUS_OKAY        | 1    | 表示这个触发条件是从低电恢复到正常电量。       |
| BATTERY_STATUS_LOW_OR_OKAY | 2    | 表示这个触发条件是从低电恢复到正常电量或者低电告警。 |

## StorageRequest

触发延迟回调的存储状态。

**系统能力**：SystemCapability.ResourceSchedule.WorkScheduler

| 名称                        | 值  | 说明                             |
| ------------------------- | ---- | ------------------------------ |
| STORAGE_LEVEL_LOW         | 0    | 表示这个触发条件是存储空间不足。               |
| STORAGE_LEVEL_OKAY        | 1    | 表示这个触发条件是从存储空间不足恢复到正常。         |
| STORAGE_LEVEL_LOW_OR_OKAY | 2    | 表示这个触发条件是存储空间不足或者从存储空间不足恢复到正常。 |