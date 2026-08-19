# getCountryCode

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getCountryCode

```TypeScript
function getCountryCode(): string
```

获取设备的国家码。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getCountryCode(): string--><!--Device-wifiManager-function getCountryCode(): string-End-->

**系统能力：** SystemCapability.Communication.WiFi.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回此设备的国家码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2401000](../errorcode-wifi.md#2401000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let code = wifiManager.getCountryCode();
    console.info("code:" + code);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

