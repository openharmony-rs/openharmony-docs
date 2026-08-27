# addSimMessage（系统接口）

## 导入模块

```TypeScript
```

## addSimMessage

```TypeScript
function addSimMessage(options: SimMessageOptions, callback: AsyncCallback<void>): void
```

添加SIM卡消息，sim卡消息满，添加报错。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.RECEIVE_SMS and ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SimMessageOptions](arkts-telephony-sms-simmessageoptions-i-sys.md) | 是 | SIM卡消息选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 添加SIM卡消息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let simMessageOptions: sms.SimMessageOptions = {
    slotId: 0,
    smsc: "test",
    pdu: "xxxxxx",
    status: sms.SimMessageStatus.SIM_MESSAGE_STATUS_READ
};
sms.addSimMessage(simMessageOptions, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## addSimMessage

```TypeScript
function addSimMessage(options: SimMessageOptions): Promise<void>
```

添加SIM卡消息，sim卡消息满，添加报错。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.RECEIVE_SMS and ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SimMessageOptions](arkts-telephony-sms-simmessageoptions-i-sys.md) | 是 | SIM卡消息选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回添加的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let simMessageOptions: sms.SimMessageOptions = {
    slotId: 0,
    smsc: "test",
    pdu: "xxxxxx",
    status: sms.SimMessageStatus.SIM_MESSAGE_STATUS_READ
};
sms.addSimMessage(simMessageOptions).then(() => {
    console.info(`addSimMessage success.`);
}).catch((err: BusinessError) => {
    console.error(`addSimMessage failed, promise: err->${JSON.stringify(err)}`);
});
```
