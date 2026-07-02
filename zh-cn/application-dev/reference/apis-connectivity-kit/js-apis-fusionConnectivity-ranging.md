# @ohos.FusionConnectivity.ranging（测距模块）

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

本模块基于近场链路通信技术，为应用提供设备测距功能，主要功能特性包括：

- 支持近场链路（星闪HADM）测距类型，实现高精度距离测量。
- 支持主动测距模式，获取目标设备的距离、角度和信号强度信息。
- 支持被动测距模式，设备可作为测距信标被其他设备发现和测量。
- 支持测距状态变化订阅，实时获取测距开始、停止等状态通知。

> **说明：**
>
> - 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { ranging } from '@kit.ConnectivityKit';
```

## ranging.isRangingSupported

isRangingSupported(): boolean

判断本机设备是否支持测距功能，若该接口返回值是false，该文件内的其他接口均无法使用。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**返回值**：

| 类型     | 说明                                       |
| ------- | ---------------------------------------- |
| boolean | 是否支持测距功能。true表示支持测距功能，false表示不支持测距功能。 |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';
let isSupport = ranging.isRangingSupported();
console.info(`This device support ranging: ${isSupport}`);
```

## ranging.getRangingCapability

getRangingCapability(): Promise&lt;RangingCapabilitySupported&gt;

查询本机设备是否支持具体的测距能力，使用Promise异步返回具体的测距能力是否支持的结果。
- 建议先使用[isRangingSupported](#rangingisRangingSupported)判断西南是否支持测距功能。仅在支持的情况下才能使用融合短距测距模块的功能。
- 异步回调结果返回后，才能基于具体的测距能力判断是否可以发起相关能力的测距，如[nearlinkHadm](#rangingRangingCapabilitySupported)值为true时，可以调用启动测距接口发起对星闪HADM的测距，如果[nearlinkHadm](#rangingRangingCapabilitySupported)值为false, 调用发起测距或者启动被动测距时，相关接口会返回测距能力不支持。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**返回值**：

| 类型                      | 说明               |
| ----------------------- | ------------------ |
| Promise&lt;RangingCapabilitySupported&gt; | Promise对象，返回设备支持的测距能力信息。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                             |
| -------- | ---------------------------------- |
| 201      | Permission denied.                 |
| 801      | Capability not supported.          |
| 34900099 | Internal error.                    |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

ranging.getRangingCapability().then((capability) => {
  console.info(`nearlink HADM supported: ${capability.nearlinkHadm}`);
}).catch((err) => {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
});
```

## ranging.startRanging

startRanging(params: RangingParams, callback: Callback&lt;RangingResult&gt;): void

与指定设备开始测距。

- 若已与目标设备建立链路连接，则直接开始测距。
- 若未连接，该接口将执行以下流程：
  1. 尝试建立连接并进行配对/加密操作。
  2. 查询服务以确认设备支持测距，确认后开始测距。
- 测距状态更新通过onRangingStateChange回调通知。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名          | 类型                                   | 必填 | 说明                    |
| ------------- | ------------------------------------ | ---- | --------------------- |
| params        | [RangingParams](#rangingrangingparams)            | 是   | 测距参数，包含设备地址和测距类型。 |
| callback      | Callback&lt;[RangingResult](#rangingrangingresult)&gt; | 是   | 测距结果回调。              |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                    |
| -------- | --------------------------------------------------------- |
| 201      | Permission denied.                                         |
| 801      | api not supported.                                        |
| 34900051 | Ranging already initiated by device.                        |
| 34900052 | Ranging service capability not supported.                   |
| 34900053 | The ranging service in use is not enabled (e.g., the switch is off). |
| 34900054 | Parameters do not conform to requirements, deviceId is invalid. |
| 34900099 | Internal error.                                           |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let params = {
  deviceId: "11:22:33:44:55:66",
  capabilityType: ranging.RangingTypes.NEARLINK_HADM
};

ranging.startRanging(params, (result) => {
  console.info(`deviceId: ${result.deviceId}`);
  console.info(`distance value: ${result.distance.value}`);
  console.info(`distance confidence: ${result.distance.confidence}`);
  console.info(`angle value: ${result.angle.value}`);
  console.info(`rssi: ${result.rssi}`);
});

ranging.onRangingStateChange((stateInfo) => {
  console.info(`ranging state: ${stateInfo.state}`);
  console.info(`ranging cause: ${stateInfo.cause}`);
});
```

## ranging.stopRanging

stopRanging(callback: Callback&lt;RangingResult&gt;, params?: RangingParams): void

停止正在进行的测距操作。

- 若未指定目标设备，则停止与该callback关联的所有设备的测距。
- 若指定了目标设备，则仅停止该设备的测距。
- 此方法同时释放已占用的资源。为实现正确的资源管理，startRanging后必须调用stopRanging以避免资源泄漏。
- 状态变化通过onRangingStateChange回调通知。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名    | 类型                                         | 必填 | 说明                      |
| ------- | ------------------------------------------ | ---- | ----------------------- |
| callback | Callback&lt;[RangingResult](#rangingrangingresult)&gt; | 是   | 测距结果回调。                |
| params   | [RangingParams](#rangingrangingparams)                | 否   | 测距参数，包含deviceId和测距类型。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                                   |
| -------- | ------------------------------------------------------------------------ |
| 201      | Permission denied.                                                         |
| 801      | Capability not supported.                                                  |
| 34000050 | Ranging not initiated by device.                                            |
| 34900052 | Ranging service capability not supported.                                   |
| 34900054 | Parameters do not conform to requirements, callback not previously used or invalid deviceId. |
| 34900099 | Internal error.                                                            |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let params = {
  deviceId: "11:22:33:44:55:66",
  capabilityType: ranging.RangingTypes.NEARLINK_HADM
};

// stop specific device ranging
ranging.stopRanging((result) => {
  console.info(`stop ranging result: ${result.deviceId}`);
}, params);

// stop all ranging
// ranging.stopRanging((result) => {
//   console.info(`stop ranging result: ${result.deviceId}`);
// });
```

## ranging.startPassiveRanging

startPassiveRanging(capabilityType: RangingTypes): Promise&lt;number&gt;

启动被动测距模式。

启动成功后返回被动测距会话的句柄标识符，并开始广播测距数据包。

返回的句柄可通过stopPassiveRanging停止被动测距广播。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名         | 类型                         | 必填 | 说明         |
| ------------ | -------------------------- | ---- | ---------- |
| capabilityType | [RangingTypes](#rangingrangingtypes) | 是   | 测距能力类型。 |

**返回值**：

| 类型               | 说明         |
| ---------------- | ---------- |
| Promise&lt;number&gt; | Promise对象，返回测距监控句柄。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                    |
| -------- | --------------------------------------------------------- |
| 201      | Permission denied.                                         |
| 801      | api not supported.                                         |
| 34900052 | Ranging service capability not supported.                   |
| 34900053 | The ranging service in use is not enabled (e.g., the switch is off). |
| 34900099 | Internal error.                                           |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

ranging.startPassiveRanging(ranging.RangingTypes.NEARLINK_HADM).then((handle) => {
  console.info(`start passive ranging success, handle: ${handle}`);
  // store handle for stopPassiveRanging
}).catch((err) => {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
});
```

## ranging.stopPassiveRanging

stopPassiveRanging(handle: number, capabilityType: RangingTypes): void

停止被动测距模式。

根据指定的句柄和测距能力类型停止被动测距广播并清理相关资源。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名         | 类型                         | 必填 | 说明         |
| ------------ | -------------------------- | ---- | ---------- |
| handle       | number                     | 是   | 测距监控句柄。   |
| capabilityType | [RangingTypes](#rangingrangingtypes) | 是   | 测距能力类型。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                                   |
| -------- | ------------------------------------------------------------------------ |
| 201      | Permission denied.                                                         |
| 801      | Capability not supported.                                                  |
| 34900052 | Ranging service capability not supported.                                   |
| 34900054 | Parameters do not conform to requirements (invalid handle value).           |
| 34900099 | Internal error.                                                            |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let handle = 123; // handle from startPassiveRanging
ranging.stopPassiveRanging(handle, ranging.RangingTypes.NEARLINK_HADM);
```

## ranging.onRangingStateChange

onRangingStateChange(callback: Callback&lt;RangingStateChangeInfo&gt;): void

注册测距状态变化回调，监听测距状态通知。

同时通知主动测距和被动测距操作的状态变化。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名     | 类型                                           | 必填 | 说明      |
| ------- | -------------------------------------------- | ---- | ------- |
| callback | Callback&lt;[RangingStateChangeInfo](#rangingrangingstatechangeinfo)&gt; | 是   | 测距状态回调。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息      |
| -------- | ----------- |
| 201      | Permission denied. |
| 801      | Capability not supported. |
| 34900099 | Internal error. |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

ranging.onRangingStateChange((stateInfo) => {
  console.info(`ranging state: ${stateInfo.state}`);
  console.info(`ranging cause: ${stateInfo.cause}`);
  if (stateInfo.deviceId) {
    console.info(`deviceId: ${stateInfo.deviceId}`);
  }
  if (stateInfo.handle) {
    console.info(`handle: ${stateInfo.handle}`);
  }
});
```

## ranging.offRangingStateChange

offRangingStateChange(callback?: Callback&lt;RangingStateChangeInfo&gt;): void

取消订阅测距状态变化事件。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名     | 类型                                           | 必填 | 说明      |
| ------- | -------------------------------------------- | ---- | ------- |
| callback | Callback&lt;[RangingStateChangeInfo](#rangingrangingstatechangeinfo)&gt; | 否   | 测距状态回调。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息      |
| -------- | ----------- |
| 201      | Permission denied. |
| 801      | Capability not supported. |
| 34900099 | Internal error. |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

// unsubscribe specific callback
ranging.offRangingStateChange((stateInfo) => {
  console.info(`ranging state: ${stateInfo.state}`);
});

// unsubscribe all callbacks
// ranging.offRangingStateChange();
```

## ranging.RangingParams

测距参数。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称            | 类型                     | 只读 | 可选 | 说明        |
| ------------- | ---------------------- | ---- | ---- | --------- |
| deviceId      | string                 | 否   | 否   | 测距设备地址。  |
| capabilityType | [RangingTypes](#rangingrangingtypes) | 否   | 否   | 测距能力类型。 |

## ranging.RangingStateChangeInfo

描述测距状态变化信息。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称    | 类型                                   | 只读 | 可选 | 说明        |
| ----- | ------------------------------------ | ---- | ---- | --------- |
| state  | [RangingState](#rangingrangingstate)              | 否   | 否   | 测距状态。    |
| cause  | [RangingStoppedCause](#rangingrangingstoppedcause) | 否   | 否   | 测距停止原因。  |
| deviceId | string                               | 否   | 是   | 测距设备地址。  |
| handle | number                               | 否   | 是   | 测距监控句柄。  |

## ranging.RangingResult

描述测距结果内容。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称     | 类型                               | 只读 | 可选 | 说明          |
| ------ | -------------------------------- | ---- | ---- | ----------- |
| deviceId | string                           | 否   | 否   | 测距设备地址。    |
| distance | [RangingMeasurement](#rangingrangingmeasurement) | 否   | 否   | 测距输出的距离测量结果。 |
| angle   | [RangingMeasurement](#rangingrangingmeasurement) | 否   | 否   | 测距输出的方位角。   |
| rssi    | number                           | 否   | 否   | 接收信号强度。    |

## ranging.RangingCapabilitySupported

描述设备支持的测距类型。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称         | 类型     | 只读 | 可选 | 说明                      |
| ---------- | ------ | ---- | ---- | ----------------------- |
| nearlinkHadm | boolean | 否   | 否   | 近场链路HADM测距类型是否支持。 |

## ranging.RangingMeasurement

描述测量结果。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称       | 类型                                 | 只读 | 可选 | 说明             |
| -------- | ---------------------------------- | ---- | ---- | -------------- |
| value    | number                             | 否   | 否   | 测量结果值，单位为厘米。 |
| confidence | [RangingConfidence](#rangingrangingconfidence) | 否   | 否   | 测量结果的置信度。   |

## ranging.RangingTypes

枚举，测距能力类型。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称           | 值   | 说明                                        |
| ------------ | ---- | ----------------------------------------- |
| NEARLINK_HADM | 1    | 近场链路HADM测距类型。此过程将触发自动链路建立。       |

## ranging.RangingState

枚举，测距状态。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称           | 值   | 说明      |
| ------------ | ---- | ------- |
| RANGING_STOPPED | 0   | 测距状态为已停止。 |
| RANGING_STARTED | 1   | 测距状态为已启动。 |

## ranging.RangingStoppedCause

枚举，测距停止原因。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称              | 值   | 说明        |
| --------------- | ---- | --------- |
| NO_ERROR         | 0   | 无错误。      |
| INTERNAL_ERROR   | 1   | 发生内部错误。   |
| BUSINESS_CONFLICT | 2   | 发生业务冲突。   |
| BACKGROUND_PAUSED | 3  | 系统资源不足。   |

## ranging.RangingConfidence

枚举，测距测量置信度。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称    | 值   | 说明        |
| ----- | ---- | --------- |
| HIGH   | 0   | 高置信度测量。  |
| MEDIUM | 1   | 中置信度测量。  |
| LOW    | 2   | 低置信度测量。  |