# getAllSimMessages（系统接口）

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## getAllSimMessages

```TypeScript
function getAllSimMessages(slotId: int, callback: AsyncCallback<Array<SimShortMessage>>): void
```

获取所有SIM卡消息。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.RECEIVE_SMS

<!--Device-sms-function getAllSimMessages(slotId: int, callback: AsyncCallback<Array<SimShortMessage>>): void--><!--Device-sms-function getAllSimMessages(slotId: int, callback: AsyncCallback<Array<SimShortMessage>>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[SimShortMessage](arkts-telephony-sms-simshortmessage-i-sys.md)&gt;&gt; | 是 | 获取所有SIM卡消息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.getAllSimMessages(slotId, (err: BusinessError, data: sms.SimShortMessage[]) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getAllSimMessages

```TypeScript
function getAllSimMessages(slotId: int): Promise<Array<SimShortMessage>>
```

获取所有SIM卡消息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.RECEIVE_SMS

<!--Device-sms-function getAllSimMessages(slotId: int): Promise<Array<SimShortMessage>>--><!--Device-sms-function getAllSimMessages(slotId: int): Promise<Array<SimShortMessage>>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | SIM卡槽ID：<br/>- 0：卡槽1<br/>- 1：卡槽2 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[SimShortMessage](arkts-telephony-sms-simshortmessage-i-sys.md)&gt;&gt; | 以Promise形式返回获取的SIM短消息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let promise = sms.getAllSimMessages(slotId);
promise.then((data: sms.SimShortMessage[]) => {
    console.info(`getAllSimMessages success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getAllSimMessages failed, promise: err->${JSON.stringify(err)}`);
});
```

