# offHotspotStaJoin（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## offHotspotStaJoin

```TypeScript
function offHotspotStaJoin(callback?: Callback<StationInfo>): void
```

取消注册热点STA加入事件。 如果未指定callback参数，将取消注册该事件关联的所有回调函数。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function offHotspotStaJoin(callback?: Callback<StationInfo>): void--><!--Device-wifiManager-function offHotspotStaJoin(callback?: Callback<StationInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;StationInfo&gt; | 否 | 状态改变回调函数。如果未指定callback参数，将取消注册该事件关联的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

