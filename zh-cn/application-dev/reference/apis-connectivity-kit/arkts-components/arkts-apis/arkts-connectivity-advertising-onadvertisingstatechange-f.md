# onAdvertisingStateChange

## 导入模块

```TypeScript
import { advertising } from '@kit.ConnectivityKit';
```

## onAdvertisingStateChange

```TypeScript
function onAdvertisingStateChange(callback: Callback<AdvertisingStateChangeInfo>): void
```

订阅星闪广播状态变化事件。使用callback异步回调。当调用[advertising.startAdvertising](arkts-connectivity-advertising-startadvertising-f.md)启动广播或[advertising.stopAdvertising](arkts-connectivity-advertising-stopadvertising-f.md)停止广播时，回调函数会被触发，返回对应的广播ID与广播状态。需与[advertising.offAdvertisingStateChange](arkts-connectivity-advertising-offadvertisingstatechange-f.md)配对使用。

应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AdvertisingStateChangeInfo](arkts-connectivity-advertising-advertisingstatechangeinfo-i.md)&gt; | 是 | 回调函数，返回广播状态变化信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
