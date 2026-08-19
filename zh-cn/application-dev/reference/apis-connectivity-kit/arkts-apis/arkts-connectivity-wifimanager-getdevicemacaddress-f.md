# getDeviceMacAddress

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getDeviceMacAddress

```TypeScript
function getDeviceMacAddress(): string[]
```

获取WLAN设备的MAC地址。必须先使能WLAN。 MAC地址是唯一的，无法更改。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_LOCAL_MAC and ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getDeviceMacAddress(): string[]--><!--Device-wifiManager-function getDeviceMacAddress(): string[]-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回WLAN设备的MAC地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let ret = wifiManager.getDeviceMacAddress();
    console.info("deviceMacAddress:" + JSON.stringify(ret));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

