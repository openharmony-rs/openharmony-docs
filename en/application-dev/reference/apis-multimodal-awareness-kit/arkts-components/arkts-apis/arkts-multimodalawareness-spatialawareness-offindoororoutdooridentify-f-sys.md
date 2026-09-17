# offIndoorOrOutdoorIdentify (System API)

## Modules to Import

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
```

## offIndoorOrOutdoorIdentify

```TypeScript
function offIndoorOrOutdoorIdentify(configParams: DistanceMeasurementConfigParams,
    callback?: Callback<DoorPositionResponse>): void
```

Unsubscribe from the results of indoor and outdoor recognition.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_SENSING_WITH_ULTRASOUND

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.MultimodalAwareness.DistanceMeasurement

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| configParams | [DistanceMeasurementConfigParams](arkts-multimodalawareness-spatialawareness-distancemeasurementconfigparams-i-sys.md) | Yes | Configuration parameters for identification inside and<br> outside the door |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DoorPositionResponse](arkts-multimodalawareness-spatialawareness-doorpositionresponse-i-sys.md)&gt; | No | Callback for identification inside and outside the door |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function can not work correctly due to<br> limited device capabilities. |
| [35100001](../errorcode-spatialAwareness.md#35100001-service-exception) | Service exception. |
| [35100003](../errorcode-spatialAwareness.md#35100003-unsubscription-failed) | Unsubscription failed. |
| [35100004](../errorcode-spatialAwareness.md#35100004-invalid-parameter) | Parameter invalid. |

**Examples**

```TypeScript
import { spatialAwareness } from '@kit.MultimodalAwarenessKit';
   console.info('call offIndoorOrOutdoorIdentify before');
   let configParams: spatialAwareness.DistanceMeasurementConfigParams = {
      deviceList: ["123456"],
      techType: 2,
      reportMode: 0,
      reportFrequency: 340
   };
   console.info('call offIndoorOrOutdoorIdentify start');
   try {
      spatialAwareness.offIndoorOrOutdoorIdentify(configParams, (data:spatialAwareness.DoorPositionResponse) => {
         console.info('result = ${data.position}');
      });
   } catch (err) {
      console.error('call offIndoorOrOutdoorIdentify failed, errCode = ' + err.code);
   }
```
