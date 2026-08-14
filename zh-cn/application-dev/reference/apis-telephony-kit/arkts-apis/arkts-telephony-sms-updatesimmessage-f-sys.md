# updateSimMessage（系统接口）

## updateSimMessage

```TypeScript
function updateSimMessage(options: UpdateSimMessageOptions, callback: AsyncCallback<void>): void
```

更新SIM卡消息。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RECEIVE_SMS and ohos.permission.SEND_MESSAGES

<!--Device-sms-function updateSimMessage(options: UpdateSimMessageOptions, callback: AsyncCallback<void>): void--><!--Device-sms-function updateSimMessage(options: UpdateSimMessageOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UpdateSimMessageOptions](arkts-telephony-sms-updatesimmessageoptions-i-sys.md) | 是 | 更新SIM卡消息选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 更新SIM卡消息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let updateSimMessageOptions: sms.UpdateSimMessageOptions = {
    slotId: 0,
    msgIndex: 1,
    newStatus: sms.SimMessageStatus.SIM_MESSAGE_STATUS_FREE,
    pdu: "xxxxxxx",
    smsc: "test"
};
sms.updateSimMessage(updateSimMessageOptions, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## updateSimMessage

```TypeScript
function updateSimMessage(options: UpdateSimMessageOptions): Promise<void>
```

更新SIM卡消息。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RECEIVE_SMS and ohos.permission.SEND_MESSAGES

<!--Device-sms-function updateSimMessage(options: UpdateSimMessageOptions): Promise<void>--><!--Device-sms-function updateSimMessage(options: UpdateSimMessageOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UpdateSimMessageOptions](arkts-telephony-sms-updatesimmessageoptions-i-sys.md) | 是 | 更新SIM卡消息选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回更新的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let updateSimMessageOptions: sms.UpdateSimMessageOptions = {
    slotId: 0,
    msgIndex: 1,
    newStatus: sms.SimMessageStatus.SIM_MESSAGE_STATUS_FREE,
    pdu: "xxxxxxx",
    smsc: "test"
};
let promise = sms.updateSimMessage(updateSimMessageOptions);
promise.then(() => {
    console.info(`updateSimMessage success.`);
}).catch((err: BusinessError) => {
    console.error(`updateSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```

