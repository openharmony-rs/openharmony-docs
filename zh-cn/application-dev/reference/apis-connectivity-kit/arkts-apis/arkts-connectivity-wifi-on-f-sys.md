# on（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## on('streamChange')

```TypeScript
function on(type: 'streamChange', callback: Callback<number>): void
```

订阅WLAN数据流改变事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** streamChange

**需要权限：** ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'streamChange' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | 是 | 状态改变回调函数。1:向下，2:向上，3:双向 |


## on('hotspotStaJoin')

```TypeScript
function on(type: 'hotspotStaJoin', callback: Callback<StationInfo>): void
```

订阅WLAN热点STA加入事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hotspotStaJoin

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaJoin' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;StationInfo&gt; | 是 | 状态改变回调函数 |


## on('hotspotStaLeave')

```TypeScript
function on(type: 'hotspotStaLeave', callback: Callback<StationInfo>): void
```

订阅WLAN热点STA离开事件。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** hotspotStaLeave

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hotspotStaLeave' | 是 | 事件名称。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;StationInfo&gt; | 是 | 状态改变回调函数 |
