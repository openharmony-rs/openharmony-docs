# onHotspotStateChange

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## onHotspotStateChange

```TypeScript
function onHotspotStateChange(callback: Callback<int>): void
```

注册热点状态改变事件。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function onHotspotStateChange(callback: Callback<int>): void--><!--Device-wifiManager-function onHotspotStateChange(callback: Callback<int>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int&gt; | 是 | 状态改变回调函数。, 0: inactive, 1: active, 2: activating, 3: de-activating |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

