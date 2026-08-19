# offWifiStateChange

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## offWifiStateChange

```TypeScript
function offWifiStateChange(callback?: Callback<int>): void
```

取消注册WLAN状态改变事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function offWifiStateChange(callback?: Callback<int>): void--><!--Device-wifiManager-function offWifiStateChange(callback?: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 否 | 状态改变回调函数。如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

