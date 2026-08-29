# findMatchingWlan

## 导入模块

```TypeScript
```

## findMatchingWlan

```TypeScript
function findMatchingWlan(
      wlanBssidArray: Array<string>, rssiThreshold: number, needStartScan: boolean): Promise<Array<MatchingWlanInfo>>
```

使用WLAN扫描结果与输入的WLAN BSSID列表进行匹配，匹配成功时返回对应的WLAN设备信息，匹配失败时返回空数组(数组长度为0)。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wlanBssidArray | Array &lt;string&gt; | 是 | 请求匹配的BSSID列表。单个字符串的长度不超过64，数组的长度不超过1000。 |
| rssiThreshold | number | 是 | RSSI阈值。只匹配RSSI大于此阈值的BSSID，取值范围为-10000至10000（单位：dBm）。 |
| needStartScan | boolean | 是 | 是否需要发起WLAN扫描。需要发起WLAN扫描设置为true。不需要发起WLAN扫描，使用最近一次WLAN扫描结果进行匹配设置为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[MatchingWlanInfo](arkts-location-geolocationmanager-matchingwlaninfo-i.md)&gt;&gt; | Promise对象，匹配成功时返回对应的WLAN设备信息，匹配失败时返回空数组(数组长度为0)。仅返回rssi最强的3个设备信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.findMatchingWlan} due to limited device capabilities. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301800](../errorcode-geoLocationManager.md#3301800-启动wi-fi或蓝牙扫描失败) | Failed to start WLAN scanning. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let wlanBssidArray: Array<string> = ["02:1b:32:23:ea:91", "02:1b:32:23:ea:93"];
  let rssiThreshold: number = -70;
  let needStartScan: boolean = true;
  geoLocationManager.findMatchingWlan(wlanBssidArray, rssiThreshold, needStartScan).then((res) => {
    console.info("WLAN BSSID Matched Result: " + JSON.stringify(res));
  })
} catch (error) {
  console.error("findMatchingWlan: errCode " + error.code + ", errMessage " + error.message);
}
```
