# getDeviceConfig（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getDeviceConfig

```TypeScript
function getDeviceConfig(networkId: int): WifiDeviceConfig
```

根据网络ID获取单条WLAN配置。

**起始版本：** 24

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function getDeviceConfig(networkId: int): WifiDeviceConfig--><!--Device-wifiManager-function getDeviceConfig(networkId: int): WifiDeviceConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | int | 是 | 待获取的WLAN配置的网络ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WifiDeviceConfig | 返回与网络ID对应的WLAN配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

