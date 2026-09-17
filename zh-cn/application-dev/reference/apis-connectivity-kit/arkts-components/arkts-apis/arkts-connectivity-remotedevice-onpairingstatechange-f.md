# onPairingStateChange

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onPairingStateChange

```TypeScript
function onPairingStateChange(callback: Callback<PairingStateParam>): void
```

订阅配对状态变化事件。使用callback异步回调。

应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PairingStateParam](arkts-connectivity-remotedevice-pairingstateparam-i.md)&gt; | 是 | 回调函数，返回订阅的配对状态变化结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
