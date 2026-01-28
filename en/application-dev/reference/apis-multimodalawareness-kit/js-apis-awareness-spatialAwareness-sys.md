# @ohos.multimodalAwareness.spatialAwareness (Spatial Awareness) (System API)
<!--Kit: Multimodal Awareness Kit-->
<!--Subsystem: MultimodalAwareness-->
<!--Owner: @dilligencer-->
<!--Designer: @zou_ye-->
<!--Tester: @judan-->
<!--Adviser: @hu-zhiqiong-->

This module provides the distance measurement awareness capability.

> **NOTE**
>
> The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Importing Modules

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## spatialAwareness.TechnologyType

Provides the type of an input signal. This API executes the corresponding algorithm based on the type of the input signal.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name               | Value  | Description                   |
| ------------------- | ---- | ----------------------- |
| BLE_RSSI            | 0    | Bluetooth strength.     |
| WIFI_RSSI           | 1    | Wi-Fi strength.     |
| ULTRASOUND          | 2    | Ultrasonic strength.     |
| NEAR_LINK           | 3    | NearLink strength. |
| BLE_WIFI_RSSI       | 4    | Bluetooth and Wi-Fi strength.|

## spatialAwareness.ReportingMode

Provides the reporting mode of the result after the distance measurement API is executed.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name                                | Value  | Description                  |
| ------------------------------------ | ---- | -----------------------|
| REPORT_MODE_PERIODIC_REPORTING       | 0    | Periodic reporting.  |
| REPORT_MODE_TRIGGERED_REPORTING      | 1    | Triggered reporting.      |

## spatialAwareness.DistanceRank

Provides the distance rank of the distance measurement result. Different ranks correspond to different distance ranges.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name                                | Value               | Description                  |
| ------------------------------------ | ------------------| -----------------------|
| RANK_ULTRA_SHORT_RANGE               | rankUltraShort    | Ultra-short distance, in cm. The value range is [0:5].   |
| RANK_SHORT_RANGE                     | rankShort         | Short distance, in cm. The value range is (5:100].    |
| RANK_SHORT_MEDIUM_RANGE              | rankMediumShort   | Medium-short distance, in cm. The value range is (100:500].|
| RANK_MEDIUM_RANGE                    | rankMedium        | Medium distance, in cm. The value range is (500:1000]. |

## spatialAwareness.DistanceMeasurementResponse

Provides the callback result after the distance measurement API is executed.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              | Type           | Read-Only  | Optional  | Description    |
| -------------------| ---------------| -------|------  |-------------|
| rank               | DistanceRank   | Yes    | No    | Indicates the distance rank.|
| distance           | float          | Yes    | No    | Indicates the distance.|
| confidence         | float          | Yes    | No    | Indicates the confidence.|
| deviceId           | string         | Yes    | No    | Indicates the device ID.|

## spatialAwareness.PositionRelativeToDoor

Enumerates the inside or outside of the door in the result returned by the door inside-outside recognition API.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              | Value            | Description                  |
| -------------------| ---------------| -----------------------|
| OUTDOOR            | 0              | Indicates outside the door.        |
| INDOOR             | 1              | Indicates inside the door.            |

## spatialAwareness.DoorPositionResponse

Provides the callback result after the door inside-outside recognition API is executed.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              | Type                  | Read-Only     | Optional      | Description    |
| -------------------| ----------------------| ----------|----------|--------|
| doorLockCode       | int                   | Yes       | No        | Indicates the door lock verification code.|
| position           | PositionRelativeToDoor| Yes       | No         | Indicates the inside and outside door location information.|
| deviceId           | string                | Yes       | No        | Indicates the device ID. |

## spatialAwareness.DistanceMeasurementConfigParams

Provides the input parameter configuration of the distance measurement API. This API executes the corresponding algorithm based on the parameter configuration.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              |  Type                  | Read-Only     | Optional      | Description    |
| -------------------| ----------------------| -----------|------------|----------|
| deviceList         | string[]              | Yes        | No| Indicates the device list.|
| techType           | TechnologyType        | Yes        | No| Indicates the signal type.|
| reportMode         | ReportingMode         | Yes        | No | Indicates the result reporting mode.|
| reportFrequency    | int                   | Yes        | No | Indicates the result reporting frequency.|

## spatialAwareness.onDistanceMeasure<sup>23+</sup>

onDistanceMeasure(configParams: DistanceMeasurementConfigParams, callback: Callback&lt;DistanceMeasurementResponse&gt;): void;

Enables distance measurement. This API triggers the execution of a distance measurement algorithm and returns the distance measurement result.

**Required permissions**: ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | Yes| Indicates the configuration parameters of the distance measurement API.|
| callback | Callback&lt;[DistanceMeasurementResponse](#spatialawarenessdistancemeasurementresponse)&gt; | Yes  | Callback function used to return the distance measurement result.                                  |

**Error codes**

For details about the error codes, see [Spatial Awareness Error Codes](errorcode-spatialAwareness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100002 | Subscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call onDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('call onDistanceMeasure start');
   try {
      spatialAwareness.onDistanceMeasure(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('result = ' + ${data.distance});
      });
   } catch (err) {
      console.error('call onDistanceMeasure failed, errCode = ' + err.code);
   }
```

## spatialAwareness.offDistanceMeasure<sup>23+</sup>

offDistanceMeasure(configParams: DistanceMeasurementConfigParams, callback?: Callback&lt;DistanceMeasurementResponse&gt;): void;

Disables distance measurement. This API stops the execution of the distance measurement algorithm.

**Required permissions**: ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | Yes| Indicates the configuration parameters of the distance measurement API.|
| callback | Callback&lt;[DistanceMeasurementResponse](#spatialawarenessdistancemeasurementresponse)&gt; | No  | Callback function used to return the distance measurement result.                                |

**Error codes**

For details about the error codes, see [Spatial Awareness Error Codes](errorcode-spatialAwareness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100003 | Unsubscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call offDistanceMeasure before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('call offDistanceMeasure start');
   try {
      spatialAwareness.offDistanceMeasure(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('result = ' + ${data.distance});
      });
   } catch (err) {
      console.error('call offDistanceMeasure failed, errCode = ' + err.code);
   }
```

## spatialAwareness.onIndoorOrOutdoorIdentify<sup>23+</sup>

onIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams, callback: Callback&lt;DoorPositionResponse&gt;): void;

Enables door inside-outside recognition. This API triggers the execution of a door inside-outside recognition algorithm and returns whether the device is inside or outside the door.

**Required permissions**: ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | Yes| Indicates the configuration parameters of the distance measurement API.|
| callback | Callback&lt;[DoorPositionResponse](#spatialawarenessdoorpositionresponse)&gt; | Yes  | Callback used to return the information on whether the device is inside or outside the door.                                  |

**Error codes**

For details about the error codes, see [Spatial Awareness Error Codes](errorcode-spatialAwareness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100002 | Subscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call onIndoorOrOutdoorIdentify before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('call onIndoorOrOutdoorIdentify start');
   try {
      spatialAwareness.onIndoorOrOutdoorIdentify(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('result = ' + ${data.position});
      });
   } catch (err) {
      console.error('call onIndoorOrOutdoorIdentify failed, errCode = ' + err.code);
   }
```

## spatialAwareness.offIndoorOrOutdoorIdentify<sup>23+</sup>

offIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams, callback?: Callback&lt;DoorPositionResponse&gt;): void;

Disables door inside-outside recognition. This API stops the execution of the door inside-outside recognition algorithm.

**Required permissions**: ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | Yes| Indicates the configuration parameters of the distance measurement API.|
| callback | Callback&lt;[DoorPositionResponse](#spatialawarenessdoorpositionresponse)&gt; | No  | Callback used to return the information on whether the device is inside or outside the door.                                  |

**Error codes**

For details about the error codes, see [Spatial Awareness Error Codes](errorcode-spatialAwareness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100003 | Unsubscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

```ts
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call offIndoorOrOutdoorIdentify before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportingMode: 0,
      reportFrequency: 340
   };
   console.info('call offIndoorOrOutdoorIdentify start');
   try {
      spatialAwareness.offIndoorOrOutdoorIdentify(configParams, (data:spatialAwareness.DistanceMeasurementResponse) => {
         console.info('result = ' + ${data.position});
      });
   } catch (err) {
      console.error('call offIndoorOrOutdoorIdentify failed, errCode = ' + err.code);
   }
```
