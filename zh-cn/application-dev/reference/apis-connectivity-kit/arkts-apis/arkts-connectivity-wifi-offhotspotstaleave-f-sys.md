# off_hotspotStaLeave（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## off('hotspotStaLeave')

```TypeScript
function off(type: 'hotspotStaLeave', callback?: Callback<StationInfo>): void
```

取消订阅WLAN热点STA离开事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hotspotStaLeave

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function off(type: 'hotspotStaLeave', callback?: Callback<StationInfo>): void--><!--Device-wifi-function off(type: 'hotspotStaLeave', callback?: Callback<StationInfo>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaLeave' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;StationInfo&gt; | 否 | 状态改变回调函数 |

