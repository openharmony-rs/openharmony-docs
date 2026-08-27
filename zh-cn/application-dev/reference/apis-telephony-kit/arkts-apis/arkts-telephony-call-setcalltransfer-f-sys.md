# setCallTransfer（系统接口）

## 导入模块

```TypeScript
```

## setCallTransfer

```TypeScript
function setCallTransfer(slotId: number, info: CallTransferInfo, callback: AsyncCallback<void>): void
```

设置呼叫转移信息。使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| info | [CallTransferInfo](arkts-telephony-call-calltransferinfo-i-sys.md) | 是 | 呼叫转移信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 以回调函数的方式返回设置呼叫转移信息的结果。 |

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

let callTransferInfo: call.CallTransferInfo = {
    transferNum: "111",
    type: call.CallTransferType.TRANSFER_TYPE_BUSY,
    settingType: call.CallTransferSettingType.CALL_TRANSFER_ENABLE
}
call.setCallTransfer(0, callTransferInfo, (err: BusinessError) => {
    if (err) {
        console.error(`setCallTransfer fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`setCallTransfer success.`);
    }
});
```


## setCallTransfer

```TypeScript
function setCallTransfer(slotId: number, info: CallTransferInfo): Promise<void>
```

设置呼叫转移信息。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| info | [CallTransferInfo](arkts-telephony-call-calltransferinfo-i-sys.md) | 是 | 呼叫转移信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式异步返回结果。 |

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

let callTransferInfo: call.CallTransferInfo = {
    transferNum: "111",
    type: call.CallTransferType.TRANSFER_TYPE_BUSY,
    settingType: call.CallTransferSettingType.CALL_TRANSFER_ENABLE
}
call.setCallTransfer(0, callTransferInfo).then(() => {
    console.info(`setCallTransfer success.`);
}).catch((err: BusinessError) => {
    console.error(`setCallTransfer fail, promise: err->${JSON.stringify(err)}`);
});
```
