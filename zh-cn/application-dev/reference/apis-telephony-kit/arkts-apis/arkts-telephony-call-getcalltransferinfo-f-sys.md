# getCallTransferInfo（系统接口）

## 导入模块

```TypeScript
```

## getCallTransferInfo

```TypeScript
function getCallTransferInfo(slotId: number, type: CallTransferType, callback: AsyncCallback<CallTransferResult>): void
```

获取呼叫转移信息。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| type | [CallTransferType](arkts-telephony-call-calltransfertype-e.md) | 是 | 呼叫转移类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CallTransferResult](arkts-telephony-call-calltransferresult-i.md)&gt; | 是 | 回调函数。返回呼叫转移信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallTransferInfo(0, call.CallTransferType.TRANSFER_TYPE_BUSY, (err: BusinessError, data: call.CallTransferResult) => {
    if (err) {
        console.error(`getCallTransferInfo fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`getCallTransferInfo success, data->${JSON.stringify(data)}`);
    }
});
```


## getCallTransferInfo

```TypeScript
function getCallTransferInfo(slotId: number, type: CallTransferType): Promise<CallTransferResult>
```

获取呼叫转移信息。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| type | [CallTransferType](arkts-telephony-call-calltransfertype-e.md) | 是 | 呼叫转移类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CallTransferResult](arkts-telephony-call-calltransferresult-i.md)&gt; | 以Promise形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallTransferInfo(0, call.CallTransferType.TRANSFER_TYPE_BUSY).then((data: call.CallTransferResult) => {
    console.info(`getCallTransferInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCallTransferInfo fail, promise: err->${JSON.stringify(err)}`);
});
```
