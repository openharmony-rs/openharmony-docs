# setWifiCapability（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## setWifiCapability

```TypeScript
function setWifiCapability(capability: WifiCapability, enable: boolean): void
```

设置WLAN能力。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.SET_WIFI_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function setWifiCapability(capability: WifiCapability, enable: boolean): void--><!--Device-wifiManager-function setWifiCapability(capability: WifiCapability, enable: boolean): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md) | 是 | 标识WLAN能力枚举。 |
| enable | boolean | 是 | 是否使能WLAN能力，{@code true}表示使能，{@code false}表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

wifiManager.setWifiCapability(wifiManager.WifiCapability.WIFI_AUTO_ENABLE, true);
```

