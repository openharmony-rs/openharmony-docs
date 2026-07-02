# @ohos.FusionConnectivity.ranging（测距模块）

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

本模块基于近场通信技术，为应用提供设备测距功能，主要功能特性包括：

- 支持近场链路星闪HADM测距类型，实现高精度距离测量。
- 支持主动测距模式，获取目标设备的距离、角度和信号强度信息。
- 支持被动测距模式，设备可作为测距信标被其他设备发现和测量。
- 支持测距状态变化订阅，实时监听设备测距开始、停止等状态通知。

> **说明：**
>
> - 本模块首批接口从API version 26开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import { ranging } from '@kit.ConnectivityKit';
```

## ranging.isRangingSupported

isRangingSupported(): boolean

判断本机设备是否支持测距特性，若该接口返回值是false，表示本机设备不支持测距特性，此时该文件内的其他接口均无法使用。

建议在调用本模块其他接口前先调用此接口进行前置检查，避免因设备不支持测距特性而导致功能异常。

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

查询本设备是否支持具体的测距能力，使用Promise异步返回具体的测距能力是否支持的结果。

使用约束：
- 建议先使用[isRangingSupported](#rangingisRangingSupported)判断本机是否支持测距特性。仅在特性支持的情况下才能使用getRangingCapability接口进行能力查询，在本机不支持测距特性时调用接口，会抛出接口不支持异常错误（错误码801）。
- 异步回调结果返回后，才能基于具体的测距能力判断是否可以发起对相关能力的测距；如果[nearlinkHadm](#rangingrangingcapabilitysupported)值为true时，可以调用启动测距接口发起对星闪HADM的测距或者调用启动被动测距；如果[nearlinkHadm](#rangingrangingcapabilitysupported)值为false，请不要再调用对应能力的主动或者被动测距接口。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**返回值**：

| 类型                      | 说明               |
| ----------------------- | ------------------ |
| Promise&lt;RangingCapabilitySupported&gt; | Promise对象，返回设备测距能力是否支持的状态信息。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                             |
| -------- | ---------------------------------- |
| 201      | Permission denied.                 |
| 801      | Capability not supported.          |
| 34900053 | The ranging service is disabled.   |

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

向指定设备发起主动测距。

该接口的执行流程取决于本设备与目标设备的连接状态：
- 若本设备已与目标设备建立了链路连接，则直接向目标设备发起测距。
- 若本设备与目标设备未连接，该接口将执行以下流程：
  1. 尝试与目标设备建立连接，连接成功后进行配对/加密操作，配对时需要用户主动在设备上操作授权；
  2. 查询目标设备是否支持对应的测距服务能力，确认服务支持后自动发起测距。

测距状态发生变化时通过[onRangingStateChange](#rangingonrangingstatechange)回调通知。测距结果通过本接口中的入参callback持续回调。由于测距结果会频繁回调上报，建议在拿到测距的结果后可根据实际需要适时调用stopRanging停止测距，之后业务需要时再次发起测距，避免无意义的测距结果上报引起本设备不必要的功耗损失。

> **说明：**
>
> - callback同时作为测距会话的标识，在调用[stopRanging](#rangingstopranging)时需传入相同的callback引用以关联会话；因此不要使用临时callback作为入参。
> - 对同一设备重复调用startRanging会提示设备已初始化测距并返回错误码34900051。
> - 同一callback可关联多个设备的测距会话，停止时可通过params指定需要停止测距的设备，否则停止测距接口将根据callback停止全部关联的设备。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名          | 类型                                   | 必填 | 说明                    |
| ------------- | ------------------------------------ | ---- | --------------------- |
| params        | [RangingParams](#rangingrangingparams)            | 是   | 测距参数，包含目标设备的地址和测距类型。 |
| callback      | Callback&lt;[RangingResult](#rangingrangingresult)&gt; | 是   | 测距结果回调，每次测距结果产生时触发回调。同时作为测距会话标识，用于stopRanging关联会话。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                    |
| -------- | -------------------------------------------------------------- |
| 201      | Permission denied.                                              |
| 801      | Capability not supported.                                       |
| 34900051 | The device has already initiated ranging.                       |
| 34900052 | The specified type of ranging service is not supported.         |
| 34900053 | The ranging service is disabled.                                |
| 34900054 | The parameter value does not meet specifications.               |
| 34900099 | Internal system error. For example, Internal object is invalid. |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let params = {
  deviceId: "11:22:33:44:55:66",
  capabilityType: ranging.RangingTypes.NEARLINK_HADM
};

let rangingCallback = (result) => {
  console.info(`deviceId: ${result.deviceId}`);
  console.info(`distance value: ${result.distance.value} cm`);
  console.info(`distance confidence: ${result.distance.confidence}`);
  console.info(`angle value: ${result.angle.value}`);
  console.info(`angle confidence: ${result.angle.confidence}`);
  console.info(`rssi: ${result.rssi}`);
};

ranging.startRanging(params, rangingCallback);

ranging.onRangingStateChange((stateInfo) => {
  console.info(`ranging state: ${stateInfo.state}`);
  console.info(`ranging cause: ${stateInfo.cause}`);
});
```

## ranging.stopRanging

stopRanging(callback: Callback&lt;RangingResult&gt;, params?: RangingParams): void

停止正在进行中的主动测距。

该接口支持以下两种停止方式：
- 若指定了params参数（包含目标设备地址和测距类型）时则仅停止与指定目标设备的测距。
- 若未指定params参数，则停止与该callback关联的所有设备的测距。

> **说明：**
>
> - 此方法同时释放测距占用的资源。为实现正确的资源管理，startRanging测距启动后必须调用stopRanging进行停止测距避免测距资源泄漏。
> - 测距状态的变化通过[onRangingStateChange](#rangingonrangingstatechange)回调进行通知。
> - callback必须与startRanging时传入的callback为同一引用对象，否则将无法停止测距。
> - 如果未调用过startRanging直接调用stopRanging将返回错误。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名    | 类型                                         | 必填 | 说明                      |
| ------- | ------------------------------------------ | ---- | ----------------------- |
| callback | Callback&lt;[RangingResult](#rangingrangingresult)&gt; | 是   | 测距结果回调，需与startRanging传入的callback为同一引用。 |
| params   | [RangingParams](#rangingrangingparams)  | 否   | 测距参数，包含deviceId和测距类型。不传入此参数时将停止与callback关联所有设备的测距。|

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                                   |
| -------- | ------------------------------------------------------------------------ |
| 201      | Permission denied.                                                         |
| 801      | Capability not supported.                                                  |
| 34900050 | The device has already initiated ranging.                                  |
| 34900052 | The specified type of ranging service is not supported.                    |
| 34900054 | The parameter value does not meet specifications.                          |
| 34900099 | Internal system error. For example, Internal object is invalid.            |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let params = {
  deviceId: "11:22:33:44:55:66",
  capabilityType: ranging.RangingTypes.NEARLINK_HADM
};

let rangingCallback = (result) => {
  console.info(`ranging result: ${result.deviceId}`);
};

// 停止指定设备的测距
ranging.stopRanging(rangingCallback, params);

// 停止该callback关联的所有设备的测距
// ranging.stopRanging(rangingCallback);
```

## ranging.startPassiveRanging

startPassiveRanging(capabilityType: RangingTypes): Promise&lt;int&gt;

启动被测距模式。

启动成功后，本设备将作为测距信标开始广播测距数据包，可被其他支持对应测距类型的主动测距设备发现和测量。

返回值为被动测距会话的句柄标识符（handle），该句柄用于：
- 在[stopPassiveRanging](#rangingstoppassiveranging)中指定要停止的被动测距会话。
- 在[onRangingStateChange](#rangingonrangingstatechange)回调的[stateInfo.handle](#rangingrangingstatechangeinfo)中标识对应的被动测距会话。

> **说明：**
>
> - 接口调用前需要通过[getRangingCapability](#ranginggetrangingcapability)确认设备支持对应的测距能力类型，否则将返回测距类型不支持错误码34900052。
> - 同一测距能力类型仅支持单次调用startPassiveRanging，成功后返回的handle对应独立的广播会话。
> - 同一测距能力如果想再次调用startPassiveRanging，需要先调用stopPassiveRanging结束本次的被动测距，如果直接再次调用，接口将返回错误码34900099。
> - 被动测距期间，主动测距设备可以通过[startRanging](#rangingstartranging)向本机发起测距。

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
| Promise&lt;int&gt; | Promise对象，返回被动测距会话的句柄标识符（handle），数值范围大于等于0。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                         |
| -------- | --------------------------------------------------------------- |
| 201      | Permission denied.                                             |
| 801      | Capability not supported.                                       |
| 34900052 | The specified type of ranging service is not supported.         |
| 34900053 | The ranging service is disabled.                                |
| 34900099 | Internal system error. For example, Internal object is invalid. |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let passiveHandle = -1;

ranging.startPassiveRanging(ranging.RangingTypes.NEARLINK_HADM).then((handle) => {
  passiveHandle = handle;
  console.info(`start passive ranging success, handle: ${handle}`);
}).catch((err) => {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
});
```

## ranging.stopPassiveRanging

stopPassiveRanging(handle: int, capabilityType: RangingTypes): void

停止被测距模式。

根据指定的句柄和测距类型停止对应的被动测距广播，并清理相关资源。

> **说明：**
>
> - handle必须为[startPassiveRanging](#rangingstartpassiveranging)返回的有效句柄。
> - 停止后该handle不再有效，不可重复使用。
> - 状态变化通过[onRangingStateChange](#rangingonrangingstatechange)回调通知。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名         | 类型                         | 必填 | 说明         |
| ------------ | -------------------------- | ---- | ---------- |
| handle       | int                     | 是   | 测距监控句柄，由startPassiveRanging返回。   |
| capabilityType | [RangingTypes](#rangingrangingtypes) | 是   | 测距能力类型，需与startPassiveRanging时传入的类型一致。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息                                                                   |
| -------- | ------------------------------------------------------------------------ |
| 201      | Permission denied.                                                         |
| 801      | Capability not supported.                                                  |
| 34900052 | The specified type of ranging service is not supported.                    |
| 34900054 | The parameter value does not meet specifications.                          |
| 34900099 | Internal system error. For example, Internal object is invalid.            |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let passiveHandle = -1; // 从startPassiveRanging获取

// 启动被动测距并保存handle
ranging.startPassiveRanging(ranging.RangingTypes.NEARLINK_HADM).then((handle) => {
  passiveHandle = handle;
});

// 停止被动测距
if (passiveHandle >= 0) {
  ranging.stopPassiveRanging(passiveHandle, ranging.RangingTypes.NEARLINK_HADM);
}
```

## ranging.onRangingStateChange

onRangingStateChange(callback: Callback&lt;RangingStateChangeInfo&gt;): void

注册测距状态变化回调，监听测距状态通知。

通知主动测距或者被动测距操作的状态变化。回调中通过不同字段区分：
- 主动测距场景：通过[stateInfo.deviceId](#rangingrangingstatechangeinfo)标识发生状态变化的设备。
- 被动测距场景：通过[stateInfo.handle](#rangingrangingstatechangeinfo)标识发生状态变化的被动测距会话。

> **说明：**
>
> - 多次调用将注册多个回调，每个回调都会收到状态变化通知。
> - 当测距状态变为[RANGING_STOPPED](#rangingrangingstate)时，[cause](#rangingrangingstoppedcause)字段表示停止原因。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名     | 类型                                           | 必填 | 说明      |
| ------- | -------------------------------------------- | ---- | ------- |
| callback | Callback&lt;[RangingStateChangeInfo](#rangingrangingstatechangeinfo)&gt; | 是   | 测距状态回调，当测距状态发生变化时触发。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息      |
| -------- | ----------- |
| 201      | Permission denied. |
| 801      | Capability not supported. |
| 34900099 | Internal system error. For example, Internal object is invalid. |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

ranging.onRangingStateChange((stateInfo) => {
  console.info(`ranging state: ${stateInfo.state}`);
  if (stateInfo.state === ranging.RangingState.RANGING_STOPPED) {
    console.info(`ranging stopped cause: ${stateInfo.cause}`);
  }
  if (stateInfo.deviceId) {
    console.info(`active ranging deviceId: ${stateInfo.deviceId}`);
  }
  if (stateInfo.handle !== undefined) {
    console.info(`passive ranging handle: ${stateInfo.handle}`);
  }
});
```

## ranging.offRangingStateChange

offRangingStateChange(callback?: Callback&lt;RangingStateChangeInfo&gt;): void

取消订阅测距状态变化事件。

> **说明：**
>
> - 若传入callback参数，则仅取消注册该callback的订阅。
> - 若不传入callback参数，则取消所有已注册的测距状态变化回调。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

**需要权限**：ohos.permission.ACCESS_NEARLINK

**参数**：

| 参数名     | 类型                                           | 必填 | 说明      |
| ------- | -------------------------------------------- | ---- | ------- |
| callback | Callback&lt;[RangingStateChangeInfo](#rangingrangingstatechangeinfo)&gt; | 否   | 测距状态回调。传入时取消该回调的订阅；不传入时取消所有已注册的回调。 |

**错误码**：

以下错误码的详细介绍请参考[融合短距服务子系统错误码](../apis-connectivity-kit/errorcode-fusionConnectivity.md)。

| 错误码ID | 错误信息      |
| -------- | ----------- |
| 201      | Permission denied. |
| 801      | Capability not supported. |
| 34900099 | 34900099 - Internal system error. For example, Internal object is invalid. |

**示例**：

```js
import { ranging } from '@kit.ConnectivityKit';

let stateCallback = (stateInfo) => {
  console.info(`ranging state: ${stateInfo.state}`);
};

// 注册订阅
ranging.onRangingStateChange(stateCallback);

// 取消指定回调的订阅
ranging.offRangingStateChange(stateCallback);

// 取消所有已注册回调的订阅
// ranging.offRangingStateChange();
```

## ranging.RangingParams

测距参数，用于指定主动测距的目标设备和测距类型。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称            | 类型                     | 只读 | 可选 | 说明        |
| ------------- | ---------------------- | ---- | ---- | --------- |
| deviceId      | string                 | 否   | 否   | 目标测距设备的地址，格式为MAC地址（如"11:22:33:44:55:66"）。  |
| capabilityType | [RangingTypes](#rangingrangingtypes) | 否   | 否   | 测距能力类型，指定使用的测距技术。 |

## ranging.RangingStateChangeInfo

描述测距状态变化信息，主动测距和被动测距的状态变化共用此结构。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称    | 类型                                   | 只读 | 可选 | 说明        |
| ----- | ------------------------------------ | ---- | ---- | --------- |
| state  | [RangingState](#rangingrangingstate)              | 否   | 否   | 测距状态。    |
| cause  | [RangingStoppedCause](#rangingrangingstoppedcause) | 否   | 否   | 测距停止原因，仅在state为RANGING_STOPPED时有意义。  |
| deviceId | string                               | 否   | 是   | 测距设备地址，主动测距场景下标识发生状态变化的目标设备。  |
| handle | int                               | 否   | 是   | 测距监控句柄，被动测距场景下标识发生状态变化的被动测距会话。  |

## ranging.RangingResult

描述测距结果内容，每次测距测量完成后通过[startRanging](#rangingstartranging)的callback回调返回。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称     | 类型                               | 只读 | 可选 | 说明          |
| ------ | -------------------------------- | ---- | ---- | ----------- |
| deviceId | string                           | 否   | 否   | 测距设备地址。    |
| distance | [RangingMeasurement](#rangingrangingmeasurement) | 否   | 否   | 测距输出的距离测量结果，value单位为厘米。 |
| angle   | [RangingMeasurement](#rangingrangingmeasurement) | 否   | 否   | 测距输出的方位角（Azimuth），value单位为度，取值范围0~360。   |
| rssi    | int                           | 否   | 否   | 接收信号强度指示（RSSI），单位为dBm，通常为负值。    |

## ranging.RangingCapabilitySupported

描述设备支持的测距类型。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称         | 类型     | 只读 | 可选 | 说明                      |
| ---------- | ------ | ---- | ---- | ----------------------- |
| nearlinkHadm | boolean | 否   | 否   | 近场链路星闪HADM测距类型是否支持。值为true时表示支持，可使用[startRanging](#rangingstartranging)或[startPassiveRanging](#rangingstartpassiveranging)发起星闪HADM测距。 |

## ranging.RangingMeasurement

描述测量结果，包含测量值和对应的置信度。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称       | 类型                                 | 只读 | 可选 | 说明             |
| -------- | ---------------------------------- | ---- | ---- | -------------- |
| value    | int                             | 否   | 否   | 测量结果值。距离测量时单位为厘米；角度测量时单位为度。 |
| confidence | [RangingConfidence](#rangingrangingconfidence) | 否   | 否   | 测量结果的置信度，表示本次测量值的可信程度。   |

## ranging.RangingTypes

枚举，测距能力类型。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称           | 值   | 说明                                        |
| ------------ | ---- | ----------------------------------------- |
| NEARLINK_HADM | 1    | 星闪HADM（High Accuracy Distance Measurement）测距类型。  |

## ranging.RangingState

枚举，测距状态。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称           | 值   | 说明      |
| ------------ | ---- | ------- |
| RANGING_STOPPED | 0   | 测距状态为已停止。停止原因参见[RangingStoppedCause](#rangingrangingstoppedcause)。 |
| RANGING_STARTED | 1   | 测距状态为已启动，测距正在进行中。 |

## ranging.RangingStoppedCause

枚举，测距停止原因。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称              | 值   | 说明        |
| --------------- | ---- | --------- |
| NO_ERROR         | 0   | 正常停止，无错误。通常由应用主动调用stopRanging或stopPassiveRanging触发。      |
| INTERNAL_ERROR   | 1   | 发生内部错误，测距服务异常导致停止。   |
| BUSINESS_CONFLICT | 2   | 发生业务冲突，其他服务占用导致测距停止。   |
| BACKGROUND_PAUSED | 3  | 应用退到后台时测距暂停。应用回到前台会自动恢复测距。   |

## ranging.RangingConfidence

枚举，测距测量置信度，表示测量结果值的可信程度。

**系统能力**：SystemCapability.Communication.FusionConnectivity.Core

**模型约束**：此接口仅可在Stage模型下使用。

| 名称    | 值   | 说明        |
| ----- | ---- | --------- |
| HIGH   | 0   | 高置信度测量，测量值可信度高，可直接使用。  |
| MEDIUM | 1   | 中置信度测量，测量值有一定可信度，建议结合其他信息综合判断。  |
| LOW    | 2   | 低置信度测量，测量值可信度低，建议谨慎使用或丢弃。  |
