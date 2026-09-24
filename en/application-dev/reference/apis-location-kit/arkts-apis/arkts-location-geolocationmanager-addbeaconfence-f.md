# addBeaconFence

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## addBeaconFence

```TypeScript
function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise<number>
```

Add a beacon fence.

**Since:** 20

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Location.Location.Geofence

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fenceRequest | [BeaconFenceRequest](arkts-location-geolocationmanager-beaconfencerequest-i.md) | Yes | Indicates the details of the beacon fence. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The promise returned by the function, for reporting the ID of beacon fence. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.addBeaconFence} due to limited device capabilities. |
| [3501100](../errorcode-geoLocationManager.md#3501100-failed-to-add-a-beacon-fence-because-the-location-switch-is-turned-off) | Failed to add a beacon fence because the location switch is off. |
| [3501101](../errorcode-geoLocationManager.md#3501101-failed-to-add-a-beacon-fence-because-bluetooth-is-disabled) | Failed to add a beacon fence because the bluetooth switch is off. |
| [3501601](../errorcode-geoLocationManager.md#3501601-failed-to-add-a-beacon-fence-because-the-maximum-number-is-exceeded) | The number of beacon fences exceeds the maximum. |
| [3501603](../errorcode-geoLocationManager.md#3501603-failed-to-add-a-beacon-fence-because-of-duplication) | Duplicate beacon fence information. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // The iBeacon protocol is used as an example. The format is as follows:
  // 01 byte    type = 0x02
  // 01 byte    len = 0x15 = 21
  // 16 byte    UUID
  // 02 byte    major
  // 02 byte    minor
  // 01 byte    tx power
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

  let fenceRequest: geoLocationManager.BeaconFenceRequest = {
    beacon: beacon,
    transitionCallback: (transition: geoLocationManager.GeofenceTransition) => {
      if (transition) {
        console.info("GeofenceTransition: err" + JSON.stringify(transition));
      }
    },
    fenceExtensionAbilityName: "MyFenceExtensionAbility",
  };
  geoLocationManager.addBeaconFence(fenceRequest).then((id) => {
    console.info("addBeaconFence success, fence id:" + id);
  }).catch((err: BusinessError) => {
    console.error('promise, addBeaconFence: error=' + JSON.stringify(err));
  });
} catch (error) {
  console.error("addBeaconFence: errCode" + error.code + ", errMessage" + error.message);
}
```
