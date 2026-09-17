# getHotspotBlockList（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getHotspotBlockList

```TypeScript
function getHotspotBlockList(): Array<StationInfo>
```

获取当前Wi-Fi热点的黑名单设备列表。该接口返回被热点拉黑的设备信息列表，仅在设备作为热点(AP)模式下有效。

**起始版本：** 11

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[StationInfo](arkts-connectivity-wifimanager-stationinfo-i-sys.md)&gt; | 热点的阻止列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
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
