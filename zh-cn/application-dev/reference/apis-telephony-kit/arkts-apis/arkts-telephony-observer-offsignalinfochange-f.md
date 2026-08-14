# offSignalInfoChange

## offSignalInfoChange

```TypeScript
function offSignalInfoChange(callback?: Callback<Array<SignalInformation>>): void
```

Cancel callback when the signal strength is updated.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-observer-function offSignalInfoChange(callback?: Callback<Array<SignalInformation>>): void--><!--Device-observer-function offSignalInfoChange(callback?: Callback<Array<SignalInformation>>): void-End-->

**系统能力：** SystemCapability.Telephony.StateRegistry

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;Array&lt;[SignalInformation](arkts-telephony-observer-signalinformation-t.md)&gt;&gt; | 否 | Indicates the callback to unsubscribe from the signalInfoChange event. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { radio } from '@kit.TelephonyKit';

let callback: (data: Array<radio.SignalInformation>) => void = (data: Array<radio.SignalInformation>) => {
    console.info(`onSignalInfoChange, data->${JSON.stringify(data)}`);
}
observer.onSignalInfoChange(callback);
// 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
observer.offSignalInfoChange(callback);
observer.offSignalInfoChange();
```

