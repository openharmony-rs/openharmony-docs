# getHotspotBlockList（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getHotspotBlockList

```TypeScript
function getHotspotBlockList(): Array<StationInfo>
```

获取黑名单中的所有站点。如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function getHotspotBlockList(): Array<StationInfo>--><!--Device-wifiManager-function getHotspotBlockList(): Array<StationInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;StationInfo&gt; | 黑名单中的站点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let data = wifiManager.getHotspotBlockList();
  console.info("result:" + JSON.stringify(data));
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

