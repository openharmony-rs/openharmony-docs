# getLocatingRequiredData（系统接口）

## 导入模块

```TypeScript
```

## getLocatingRequiredData

```TypeScript
function getLocatingRequiredData(config: LocatingRequiredDataConfig): Promise<Array<LocatingRequiredData>>
```

单次获取定位业务所需数据，包含WiFi蓝牙扫描信息，使用Promise方式异步返回结果。

**起始版本：** 10

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Location.Location.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [LocatingRequiredDataConfig](arkts-location-geolocationmanager-locatingrequireddataconfig-i-sys.md) | 是 | 表示获取定位所需数据时的配置参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[LocatingRequiredData](arkts-location-geolocationmanager-locatingrequireddata-i-sys.md)&gt;&gt; | 以Promise形式返回定位业务所需数据，包含WiFi蓝牙扫描信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.getLocatingRequiredData} due to limited device capabilities. |
| [3301800](../errorcode-geoLocationManager.md#3301800-启动wi-fi或蓝牙扫描失败) | Failed to start WiFi or Bluetooth scanning. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: geoLocationManager.LocatingRequiredDataConfig = { 'type': 1, 'needStartScan': true, 'scanInterval': 10000 };
try {
  geoLocationManager.getLocatingRequiredData(config).then((result) => {
    console.info('getLocatingRequiredData return: ' + JSON.stringify(result));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getLocatingRequiredData: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
