# isWlanBssidMatched

## 导入模块

```TypeScript
```

## isWlanBssidMatched

```TypeScript
function isWlanBssidMatched(
      wlanBssidArray: Array<string>, rssiThreshold: number, needStartScan: boolean): Promise<boolean>
```

判断指定的BSSID是否存在于最新的WLAN扫描结果里。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| wlanBssidArray | Array & lt;string & gt; | 是 | 请求匹配的BSSID列表。单个字符串的长度不超过64，数组的长度不超过1000。 |
| rssiThreshold | number | 是 | RSSI阈值。只匹配RSSI大于此阈值的BSSID，取值范围为-10000至10000（单位：dBm）。 |
| needStartScan | boolean | 是 | 是否需要发起WLAN扫描。需要发起WLAN扫描设置为true。不需要发起WLAN扫描，使用最近一次WLAN扫描结果进行匹配设置为false。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 表示匹配是否成功。当扫描结果中存在wlanBssidArray中的任意BSSID，且其RSSI值高于rssiThreshold时，返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call \\${geoLocationManager.isWlanBssidMatched} due to limited device capabilities. |
| [3301100](../errorcode-geoLocationManager.md#3301100-位置功能的开关未开启导致功能失败) | The location switch is off. |
| [3301800](../errorcode-geoLocationManager.md#3301800-启动wi-fi或蓝牙扫描失败) | Failed to start WiFi scanning. |

**示例**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let wlanBssidArray: Array<string> = ["02:1b:32:23:ea:91", "02:1b:32:23:ea:93"];
  let rssiThreshold: number = -70;
  let needStartScan: boolean = true;
  geoLocationManager.isWlanBssidMatched(wlanBssidArray, rssiThreshold, needStartScan).then((res) => {
    console.info("Wlan Bssid Matched Result:" + res);
  })
} catch (error) {
  console.error("isWlanBssidMatched: errCode" + error.code + ", errMessage" + error.message);
}
```
