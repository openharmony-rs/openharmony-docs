# getCallTransferInfo

## 导入模块

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## getCallTransferInfo

```TypeScript
function getCallTransferInfo(type: CallTransferType, number: string): Promise<CallTransferResult>
```

获取电话号码的呼叫转移状态。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_CALL_TRANSFER_INFO

<!--Device-call-function getCallTransferInfo(type: CallTransferType, number: string): Promise<CallTransferResult>--><!--Device-call-function getCallTransferInfo(type: CallTransferType, number: string): Promise<CallTransferResult>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [CallTransferType](arkts-telephony-call-calltransfertype-e-sys.md) | 是 | 指示要获取哪种类型的呼叫转移。 |
| number | string | 是 | 指示用于获取呼叫转移状态的号码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CallTransferResult](arkts-telephony-call-calltransferresult-i-sys.md)&gt; | Promise对象，返回呼叫转移结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8401002](../errorcode-telephony.md#8401002-输入号码错误) | Invalid input call number. |
| [8401003](../errorcode-telephony.md#8401003-操作频繁) | Operation too frequent. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { call } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let type: call.CallTransferType = call.CallTransferType.TRANSFER_TYPE_UNCONDITIONAL;
let number: string = "138xxxxxxxx";

call.getCallTransferInfo(type, number)
    .then((data: call.CallTransferResult) => {
        console.info(`getCallTransferInfo success, data->${JSON.stringify(data)}`);
    })
    .catch((err:BusinessError) => {
        console.error(`getCallTransferInfo fail, 本次操作异常，err->Code${err.code}, message:${err.message}请稍后重试。`);
    });
```

