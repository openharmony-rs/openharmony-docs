# getSmsSegmentsInfo（系统接口）

## 导入模块

```TypeScript
```

## getSmsSegmentsInfo

```TypeScript
function getSmsSegmentsInfo(slotId: number, message: string, force7bit: boolean, callback: AsyncCallback<SmsSegmentsInfo>): void
```

获取短信段信息。使用callback异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | SIM卡槽ID：   - 0：卡槽1   - 1：卡槽2 |
| message | string | 是 | 消息。 |
| force7bit | boolean | 是 | 是否使用7 bit编码，默认false。   -true：是   -false：否 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmsSegmentsInfo](arkts-telephony-sms-smssegmentsinfo-i-sys.md)&gt; | 是 | 指示用于获取短信短信息的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

let slotId: number = 0;
sms.getSmsSegmentsInfo(slotId, "message", false, (err: BusinessError, data: sms.SmsSegmentsInfo) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getSmsSegmentsInfo

```TypeScript
function getSmsSegmentsInfo(slotId: number, message: string, force7bit: boolean): Promise<SmsSegmentsInfo>
```

获取短信段信息。使用Promise异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | SIM卡槽ID：   - 0：卡槽1   - 1：卡槽2 |
| message | string | 是 | 消息。 |
| force7bit | boolean | 是 | 是否使用7 bit编码，默认false。   -true：是   -false：否 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SmsSegmentsInfo](arkts-telephony-sms-smssegmentsinfo-i-sys.md)&gt; | 以Promise形式返回短信段信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
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

let slotId: number = 0;
let promise = sms.getSmsSegmentsInfo(slotId, "message", false);
promise.then((data: sms.SmsSegmentsInfo) => {
    console.info(`getSmsSegmentsInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSmsSegmentsInfo failed, promise: err->${JSON.stringify(err)}`);
});
```
