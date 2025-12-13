# @ohos.multimodalAwareness.spatialAwareness (空间感知)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

本模块提供对测距的感知能力。

> **说明：**
>
> 本模块首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## spatialAwareness.TechnologyType

提供信号类型。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称                | 值   | 说明                    |
| ------------------- | ---- | ----------------------- |
| BLE_RSSI            | 0    | 表示蓝牙强度。      |
| WIFI_RSSI           | 1    | 表示WIFI强度。      |
| ULTRASOUND          | 2    | 表示超声强度。      |
| NEAR_LINK           | 3    | 表示星闪强度。  |
| BLE_WIFI_RSSI       | 4    | 表示蓝牙和WIFI强度。|

## spatialAwareness.ReportingMode

测距后返回结果的上报模式。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称                                 | 值   | 说明                   |
| ------------------------------------ | ---- | -----------------------|
| REPORT_MODE_PERIODIC_REPORTING       | 0    | 表示周期性上报。   |
| REPORT_MODE_TRIGGERED_REPORTING      | 1    | 表示触发式上报。       |

## spatialAwareness.DistanceRank

距离档位。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称                                 | 值                | 说明                   |
| ------------------------------------ | ------------------| -----------------------|
| RANK_ULTRA_SHORT_RANGE               | rankUltraShort    | 表示超短距。           |
| RANK_SHORT_RANGE                     | rankShort         | 表示短距。             |
| RANK_SHORT_MEDIUM_RANGE              | rankMediumShort   | 表示中短距。           |
| RANK_MEDIUM_RANGE                    | rankMedium        | 表示中距。             |

## spatialAwareness.DistanceMeasurementResponse

测距结果。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称               | 类型            | 只读   | 可选   | 说明     |
| -------------------| ---------------| -------|------  |-------------|
| rank               | DistanceRank   | 是     | 否     | 表示距离档位。|
| distance           | float          | 是     | 否     | 表示距离。|
| confidence         | float          | 是     | 否     | 表示置信度。|
| deviceId           | string         | 是     | 否     | 表示设备Id号。|

## spatialAwareness.PositionRelativeToDoor

门内或者门外。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称               | 值             | 说明                   |
| -------------------| ---------------| -----------------------|
| OUTDOOR            | 0              | 表示门外。         |
| INDOOR             | 1              | 表示门内。             |

## spatialAwareness.DoorPositionResponse

门位置信息。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称               | 类型                   | 只读      | 可选       | 说明     |
| -------------------| ----------------------| ----------|----------|--------|
| doorLockCode       | int                   | 是        | 否         | 表示门锁校验码。|
| position           | PositionRelativeToDoor| 是        | 否          | 表示门内外位置信息。|
| deviceId           | string                | 是        | 否         | 表示设备Id号。  |

## spatialAwareness.DistanceMeasurementConfigParams

测距接口配置参数。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

| 名称               |  类型                   | 只读      | 可选       | 说明     |
| -------------------| ----------------------| -----------|------------|----------|
| deviceList         | string[]              | 是         | 否 | 表示设备列表。|
| techType           | TechnologyType        | 是         | 否 | 表示信号类型。|
| reportMode         | ReportingMode         | 是         | 否  | 表示结果上报模式。|

## spatialAwareness.onDistanceMeasure

onDistanceMeasure(configParams: DistanceMeasurementConfigParams,
    callback: Callback&lt;DistanceMeasurementResponse&gt;): void;

订阅测距事件后，返回测距结果。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | 是 | 测距接口配置参数
| callback | Callback&lt;[DistanceMeasurementResponse](#spatialawarenessdistancemeasurementresponse)&gt; | 是   | 回调函数，返回测距结果。                                   |

**错误码**：

以下错误码的详细介绍请参见[空间感知错误码](errorcode-spatialAwareness.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100002 | Subscription failed. |
| 35100004 | Parameter invalid. |

**示例**：

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('calllOnDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('calllOnDistanceMeasure start');
   try {
      spatialAwareness.onDistanceMeasure(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('distanceMeasure result' + ${data.distance});
      });
   } catch (err) {
      console.error('distanceMeasure:, errCode = ' + err.code);
   }
```

## spatialAwareness.offDistanceMeasure

offDistanceMeasure(configParams: DistanceMeasurementConfigParams,
    callback?: Callback&lt;DistanceMeasurementResponse&gt;): void;

取消订阅测距事件。取消订阅测距事件后，不会发生测距。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | 是 | 测距接口配置参数
| callback | Callback&lt;[DistanceMeasurementResponse](#spatialawarenessdistancemeasurementresponse)&gt; | 是   | 回调函数，返回测距结果。                                 |

**错误码**：

以下错误码的详细介绍请参见[空间感知错误码](errorcode-spatialAwareness.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100003 | Unsubscription failed. |
| 35100004 | Parameter invalid. |

**示例**：

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('calllOnDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('calllOnDistanceMeasure start');
   try {
      spatialAwareness.offDistanceMeasure(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('distanceMeasure result' + ${data.distance});
      });
   } catch (err) {
      console.error('distanceMeasure:, errCode = ' + err.code);
   }
```

## spatialAwareness.onIndoorOrOutdoorIdentify

onIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams,
    callback: Callback&lt;DoorPositionResponse&gt;): void;
订阅门内外识别事件后返回结果。返回设备在门内还是门外的信息。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | 是 | 测距接口配置参数
| callback | Callback&lt;[DoorPositionResponse](#spatialawarenessdoorpositionresponse)&gt; | 是   | 回调函数，返回门内外信息。                                   |

**错误码**：

以下错误码的详细介绍请参见[空间感知错误码](errorcode-spatialAwareness.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100002 | Subscription failed. |
| 35100004 | Parameter invalid. |

**示例**：

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('calllOnDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('calllOnDistanceMeasure start');
   try {
      spatialAwareness.onIndoorOrOutdoorIdentify(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('distanceMeasure result' + ${data.position});
      });
   } catch (err) {
      console.error('distanceMeasure:, errCode = ' + err.code);
   }
```

## spatialAwareness.offIndoorOrOutdoorIdentify

offIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams,
    callback?: Callback&lt;DoorPositionResponse&gt;): void;

取消识别门内外订阅事件。不返回门内外信息。

**系统能力**：SystemCapability.MultimodalAwareness.DistanceMeasurement

**参数**：

| 参数名   | 类型                             | 必填 | 说明                                                         |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | 是 | 测距接口配置参数
| callback | Callback&lt;[DoorPositionResponse](#spatialawarenessdoorpositionresponse)&gt; | 是   | 回调函数，返回门内外信息。                                   |

**错误码**：

以下错误码的详细介绍请参见[空间感知错误码](errorcode-spatialAwareness.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 202      | Not system application.
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100003 | Unsubscription failed. |
| 35100004 | Parameter invalid. |

**示例**：

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('calllOnDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('calllOnDistanceMeasure start');
   try {
      spatialAwareness.offIndoorOrOutdoorIdentify(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('distanceMeasure result' + ${data.position});
      });
   } catch (err) {
      console.error('distanceMeasure:, errCode = ' + err.code);
   }
```
