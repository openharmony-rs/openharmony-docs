# onRangingStateChange

## 导入模块

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## onRangingStateChange

```TypeScript
function onRangingStateChange(callback: Callback<RangingStateChangeInfo>): void
```

注册测距状态变化回调，监听测距状态通知。

通知主动测距或者被动测距操作的状态变化。回调中通过不同字段区分：

主动测距场景：通过[stateInfo.deviceId](arkts-connectivity-ranging-rangingstatechangeinfo-i.md)标识发生状态变化的设备。被动测距场景：通过[stateInfo.handle](arkts-connectivity-ranging-rangingstatechangeinfo-i.md)标识发生状态变化的被动测距会话。

多次调用将注册多个回调，每个回调都会收到状态变化通知。

当测距状态变为[RANGING_STOPPED](arkts-connectivity-ranging-rangingstate-e.md)时，[cause](arkts-connectivity-ranging-rangingstoppedcause-e.md)字段表示停止原因。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.FusionConnectivity.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingStateChangeInfo](arkts-connectivity-ranging-rangingstatechangeinfo-i.md)&gt; | 是 | 测距状态回调，当测距状态发生变化时触发。该参数可用于[offRangingStateChange](arkts-connectivity-ranging-offrangingstatechange-f.md)接口的入参取消注册测距状态回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-操作失败) | Internal system error. For example, Internal object is invalid. |
