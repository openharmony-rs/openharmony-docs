# @ohos.multimodalAwareness.spatialAwareness (Spatial Awareness)
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

Provides the signal type.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name               | Value  | Description                   |
| ------------------- | ---- | ----------------------- |
| BLE_RSSI            | 0    | Bluetooth strength.     |
| WIFI_RSSI           | 1    | Wi-Fi strength.     |
| ULTRASOUND          | 2    | Ultrasonic strength.     |
| NEAR_LINK           | 3    | NearLink strength. |
| BLE_WIFI_RSSI       | 4    | Bluetooth and Wi-Fi strength.|

## spatialAwareness.ReportingMode

Reporting mode of the returned result after distance measurement.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name                                | Value  | Description                  |
| ------------------------------------ | ---- | -----------------------|
| REPORT_MODE_PERIODIC_REPORTING       | 0    | Periodic reporting.  |
| REPORT_MODE_TRIGGERED_REPORTING      | 1    | Triggered reporting.      |

## spatialAwareness.DistanceRank

Distance rank.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name                                | Value               | Description                  |
| ------------------------------------ | ------------------| -----------------------|
| RANK_ULTRA_SHORT_RANGE               | rankUltraShort    | Ultra-short distance.          |
| RANK_SHORT_RANGE                     | rankShort         | Short distance.            |
| RANK_SHORT_MEDIUM_RANGE              | rankMediumShort   | Medium-short distance.          |
| RANK_MEDIUM_RANGE                    | rankMedium        | Medium distance.            |

## spatialAwareness.DistanceMeasurementResponse

Distance measurement result.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              | Type           | Read-Only  | Optional  | Description    |
| -------------------| ---------------| -------|------  |-------------|
| rank               | DistanceRank   | Yes    | No    | Indicates the distance rank.|
| distance           | float          | Yes    | No    | Indicates the distance.|
| confidence         | float          | Yes    | No    | Indicates the confidence.|
| deviceId           | string         | Yes    | No    | Indicates the device ID.|

## spatialAwareness.PositionRelativeToDoor

Indicates inside or outside the door.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              | Value            | Description                  |
| -------------------| ---------------| -----------------------|
| OUTDOOR            | 0              | Indicates outside the door.        |
| INDOOR             | 1              | Indicates inside the door.            |

## spatialAwareness.DoorPositionResponse

Door location information.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              | Type                  | Read-Only     | Optional      | Description    |
| -------------------| ----------------------| ----------|----------|--------|
| doorLockCode       | int                   | Yes       | No        | Indicates the door lock verification code.|
| position           | PositionRelativeToDoor| Yes       | No         | Indicates the inside and outside door location information.|
| deviceId           | string                | Yes       | No        | Indicates the device ID. |

## spatialAwareness.DistanceMeasurementConfigParams

Indicates the configuration parameters of the distance measurement API.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

| Name              |  Type                  | Read-Only     | Optional      | Description    |
| -------------------| ----------------------| -----------|------------|----------|
| deviceList         | string[]              | Yes        | No| Indicates the device list.|
| techType           | TechnologyType        | Yes        | No| Indicates the signal type.|
| reportMode         | ReportingMode         | Yes        | No | Indicates the result reporting mode.|

## spatialAwareness.onDistanceMeasure

onDistanceMeasure(configParams: DistanceMeasurementConfigParams, callback: Callback&lt;DistanceMeasurementResponse&gt;): void;

Subscribes to the distance measurement event and returns the result.

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
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100002 | Subscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

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

offDistanceMeasure(configParams: DistanceMeasurementConfigParams, callback?: Callback&lt;DistanceMeasurementResponse&gt;): void;

Unsubscribes from a distance measurement event. After the distance measurement event is unsubscribed, distance measurement does not occur.

**System capability**: SystemCapability.MultimodalAwareness.DistanceMeasurement

**Parameters**

| Name  | Type                            | Mandatory| Description                                                        |
| -------- | -------------------------------- | ---- | ------------------------------------------------------------ |
| configParams | DistanceMeasurementConfigParams | Yes| Indicates the configuration parameters of the distance measurement API.|
| callback | Callback&lt;[DistanceMeasurementResponse](#spatialawarenessdistancemeasurementresponse)&gt; | Yes  | Callback function used to return the distance measurement result.                                |

**Error codes**

For details about the error codes, see [Spatial Awareness Error Codes](errorcode-spatialAwareness.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100003 | Unsubscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

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

onIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams, callback: Callback&lt;DoorPositionResponse&gt;): void;
Subscribes to inside and outside door recognition events and returns the result. Returns whether the device is inside or outside the door.

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
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100002 | Subscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

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

offIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams, callback?: Callback&lt;DoorPositionResponse&gt;): void;

Unsubscribes from inside and outside door recognition events. No inside and outside door recognition events information is returned.

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
| 202      | Not system application. |
| 801      | Capability not supported. Function can not work correctly due to limited device capabilities. |
| 35100001 | Service exception. |
| 35100003 | Unsubscription failed. |
| 35100004 | Parameter invalid. |

**Example**:

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
