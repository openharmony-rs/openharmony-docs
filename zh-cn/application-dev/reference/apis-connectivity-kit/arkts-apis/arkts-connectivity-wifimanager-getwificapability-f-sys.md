# getWifiCapability（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getWifiCapability

```TypeScript
function getWifiCapability(capability: WifiCapability): boolean
```

获取WLAN支持的能力。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_WIFI_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| capability | [WifiCapability](arkts-connectivity-wifimanager-wificapability-e.md) | 是 | 标识WLAN能力枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果指定的能力已使能，返回{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

let result = wifiManager.getWifiCapability(wifiManager.WifiCapability.WIFI_AUTO_ENABLE);
console.info("result:" + result);
```
