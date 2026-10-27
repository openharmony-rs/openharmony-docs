# onAcbStateChange

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onAcbStateChange

```TypeScript
function onAcbStateChange(callback: Callback<AcbStateParam>): void
```

订阅逻辑链路连接状态变化事件。使用callback异步回调。适用于需要在逻辑链路建立或断开时触发相应处理的场景，如数据传输前的链路就绪检查或断连后的资源清理。与[remoteDevice.onConnectionStateChange](arkts-connectivity-remotedevice-onconnectionstatechange-f.md#onconnectionstatechange-1)监听设备层级连接状态不同，本接口监听逻辑链路层级的连接状态。

应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-remoteDevice-function onAcbStateChange(callback: Callback<AcbStateParam>): void--><!--Device-remoteDevice-function onAcbStateChange(callback: Callback<AcbStateParam>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参见：** [offAcbStateChange](arkts-connectivity-remotedevice-offacbstatechange-f.md#offacbstatechange-1) 取消订阅逻辑链路连接状态变化事件。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AcbStateParam](arkts-connectivity-remotedevice-acbstateparam-i.md)&gt; | 是 | 回调函数，返回订阅的逻辑链路连接状态变化事件上报结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
