# getStations（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getStations

```TypeScript
function getStations(): Array<StationInfo>
```

获取连接到WLAN热点的站点列表。 此方法只能在作为WLAN热点的设备上使用。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function getStations(): Array<StationInfo>--><!--Device-wifiManager-function getStations(): Array<StationInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;StationInfo&gt; | 连接到WLAN热点的客户端列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let stations = wifiManager.getStations();
  console.info("result:" + JSON.stringify(stations));    
}catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

