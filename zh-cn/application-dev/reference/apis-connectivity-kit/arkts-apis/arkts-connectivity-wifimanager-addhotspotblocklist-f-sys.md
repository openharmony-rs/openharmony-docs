# addHotspotBlockList（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addHotspotBlockList

```TypeScript
function addHotspotBlockList(stationInfo: StationInfo): void
```

将站点添加到黑名单，该站点无法访问热点。

**起始版本：** 11

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| stationInfo | StationInfo | 是 | 将要添加到黑名单的站点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1.Incorrect parameter types. 2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let config:wifiManager.StationInfo = {
    name : "testSsid",
    macAddress : "11:22:33:44:55:66",
    ipAddress : "192.168.1.111"
  }
  // 热点开启后，才能正常将设备添加到连接阻止列表中
  wifiManager.addHotspotBlockList(config);
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
