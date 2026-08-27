# addBeaconFence

## 导入模块

```TypeScript
```

## addBeaconFence

```TypeScript
function addBeaconFence(fenceRequest: BeaconFenceRequest): Promise<number>
```

添加一个beacon围栏，并订阅地理围栏事件。使用Promise异步回调。 beacon围栏是指通过蓝牙beacon设备和手机应用配合，实现“虚拟围栏”的功能。当用户靠近或离开某个特定的beacon设备时，手机应用会收到通知。 应用可以在入参[BeaconFenceRequest](arkts-location-geolocationmanager-beaconfencerequest-i.md)中传入回调函数用于接收围栏事件；也可以传入 [FenceExtensionAbility](arkts-location-app-ability-fenceextensionability-fenceextensionability-c.md)名称，在系统识别到围栏事件发生时通知应用。 单应用添加beacon围栏上限为10，超过上限会导致添加beacon围栏失败，并抛出3501601错误码。

**起始版本：** 20

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fenceRequest | [BeaconFenceRequest](arkts-location-geolocationmanager-beaconfencerequest-i.md) | 是 | 添加beacon围栏请求参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | Promise对象，返回beacon围栏ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.addBeaconFence} due to limited device capabilities. |
| [3501100](../errorcode-geoLocationManager.md#3501100-由于位置功能开关未打开导致添加beacon围栏失败) | Failed to add a beacon fence because the location switch is off. |
| [3501101](../errorcode-geoLocationManager.md#3501101-由于蓝牙功能开关未打开导致添加beacon围栏失败) | Failed to add a beacon fence because the bluetooth switch is off. |
| [3501601](../errorcode-geoLocationManager.md#3501601-由于beacon围栏个数超过最大值限制导致添加围栏失败) | The number of beacon fences exceeds the maximum. |
| [3501603](../errorcode-geoLocationManager.md#3501603-由于存在重复的beacon围栏导致添加围栏失败) | Duplicate beacon fence information. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // 以iBeacon协议为例，格式如下
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
