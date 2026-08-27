# setMockedLocations（系统接口）

## 导入模块

```TypeScript
```

## setMockedLocations

```TypeScript
function setMockedLocations(config: LocationMockConfig): void
```

设置模拟的位置信息，后面会以该接口中携带的时间间隔上报模拟位置。

**起始版本：** 9

**需要权限：** 
- API版本20+：ohos.permission.MOCK_LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [LocationMockConfig](arkts-location-geolocationmanager-locationmockconfig-i-sys.md) | 是 | 指示位置模拟的配置参数，包含模拟位置上报的时间间隔和模拟位置数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.setMockedLocations} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-位置服务不可用) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API.<br>**适用版本：** 20+ |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

let locations: Array<geoLocationManager.Location> = [
  {
    "latitude": 30.12,
    "longitude": 120.11,
    "altitude": 123,
    "accuracy": 1,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 1000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 31.13,
    "longitude": 121.11,
    "altitude": 123,
    "accuracy": 2,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 2000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 32.14,
    "longitude": 122.11,
    "altitude": 123,
    "accuracy": 3,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 3000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 33.15,
    "longitude": 123.11,
    "altitude": 123,
    "accuracy": 4,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 4000000000,
    "additionSize": 0,
    "isFromMock": true
  },
  {
    "latitude": 34.16,
    "longitude": 124.11,
    "altitude": 123,
    "accuracy": 5,
    "speed": 5.2,
    "timeStamp": 16594326109,
    "direction": 123.11,
    "timeSinceBoot": 5000000000,
    "additionSize": 0,
    "isFromMock": true
  }
];
let config: geoLocationManager.LocationMockConfig = { "timeInterval": 5, "locations": locations };
try {
  geoLocationManager.enableLocationMock();
  geoLocationManager.setMockedLocations(config);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
