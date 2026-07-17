# offPairingStateChange

## 导入模块

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## offPairingStateChange

```TypeScript
function offPairingStateChange(callback?: Callback<PairingStateParam>): void
```

取消订阅星闪配对状态更改事件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-remoteDevice-function offPairingStateChange(callback?: Callback<PairingStateParam>): void--><!--Device-remoteDevice-function offPairingStateChange(callback?: Callback<PairingStateParam>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<PairingStateParam> | 否 | 用于监听配对状态事件的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100099 | Operation failed. |

