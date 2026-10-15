# offStateChange

## 导入模块

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## offStateChange

```TypeScript
function offStateChange(callback?: Callback<NearlinkState>): void
```

取消订阅星闪开关状态变化事件。使用callback异步回调。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-manager-function offStateChange(callback?: Callback<NearlinkState>): void--><!--Device-manager-function offStateChange(callback?: Callback<NearlinkState>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参见：** [onStateChange](arkts-connectivity-manager-onstatechange-f.md) 订阅星闪开关状态变化事件。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md)&gt; | 否 | 回调函数，返回星闪的开关状态。<br>填写该参数则取消当前callback订阅。不填写该参数则取消该事件对应的所有回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
