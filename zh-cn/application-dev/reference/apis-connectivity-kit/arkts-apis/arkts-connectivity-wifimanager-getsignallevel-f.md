# getSignalLevel

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getSignalLevel

```TypeScript
function getSignalLevel(rssi: int, band: int): int
```

根据WLAN RSSI和频段计算WLAN信号强度。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getSignalLevel(rssi: int, band: int): int--><!--Device-wifiManager-function getSignalLevel(rssi: int, band: int): int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rssi | int | 是 | 表示WLAN RSSI。 |
| band | int | 是 | 表示WLAN频段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回WLAN信号强度，范围从0到4。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let rssi = 0;
    let band = 0;
    let level = wifiManager.getSignalLevel(rssi,band);
    console.info("level:" + JSON.stringify(level));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

