# offCallStateChangeEx

## offCallStateChangeEx

```TypeScript
function offCallStateChangeEx(callback?: Callback<TelCallState>): void
```

Cancel callback when the telCall state is updated.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-observer-function offCallStateChangeEx(callback?: Callback<TelCallState>): void--><!--Device-observer-function offCallStateChangeEx(callback?: Callback<TelCallState>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;TelCallState&gt; | 否 | Indicates the callback to unsubscribe from the callStateChangeEx event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8800999](../errorcode-telephony.md#8800999-内部错误) | Unknown error. |
| [8800002](../errorcode-telephony.md#8800002-服务连接失败) | Service connection failed. |
| [8800003](../errorcode-telephony.md#8800003-系统内部错误) | System internal error. |
| [8800001](../errorcode-telephony.md#8800001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { call } from '@kit.TelephonyKit';
let callback: (data: call.TelCallState) => void = (data: call.TelCallState) => {
    console.info("on callStateChangeEx, data:" + JSON.stringify(data));
}
observer.oncallStateChangeEx(callback);
observer.offcallStateChangeEx(callback);
observer.offcallStateChangeEx();
```

