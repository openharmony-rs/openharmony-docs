# removeBeaconFence

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## removeBeaconFence

```TypeScript
function removeBeaconFence(beaconFence?: BeaconFence): Promise<void>
```

Remove a beacon fence.

**Since:** 20

**Required permissions:** 
- API version 25 and later: N/A
- API versions 20 to 24: ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Location.Location.Geofence

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| beaconFence | [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md) | No | Indicates the details of the beacon fence. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 20 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call &#36;{geoLocationManager.removeBeaconFence} due to limited device capabilities. |
| [3501602](../errorcode-geoLocationManager.md#3501602-failed-to-delete-a-beacon-fence-because-of-incorrect-information) | Failed to delete the fence due to incorrect beacon fence information. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let manufactureDataBuffer: Uint8Array = new Uint8Array([0X02, 0X15, 0X00, 0X11, 0X22, 0X33, 0X44, 0X55,
    0X66, 0X77, 0X88, 0X99, 0XAA, 0XBB, 0XCC, 0XDD, 0XEE, 0XFF, 0X11, 0X22, 0X33, 0X44, 0X55]);
  let manufactureDataMaskBuffer: Uint8Array = new Uint8Array([0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF,
    0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF, 0XFF]);

  let manufactureData: geoLocationManager.BeaconManufactureData = {
    manufactureId: 0X004C,
    manufactureData: manufactureDataBuffer.buffer,
    manufactureDataMask: manufactureDataMaskBuffer.buffer
  };

  let beacon: geoLocationManager.BeaconFence = {
    identifier: "11",
    beaconFenceInfoType: geoLocationManager.BeaconFenceInfoType.BEACON_MANUFACTURE_DATA,
    manufactureData: manufactureData
  };
  geoLocationManager.removeBeaconFence(beacon).then(() => {
    console.info("promise, removeBeaconFence success");
  })
    .catch((error: BusinessError) => {
      console.error("promise, removeBeaconFence: errCode" + error.code + ", errMessage" + error.message);
    });
} catch (error) {
  console.error("removeBeaconFence: errCode" + error.code + ", errMessage" + error.message);
}
```
