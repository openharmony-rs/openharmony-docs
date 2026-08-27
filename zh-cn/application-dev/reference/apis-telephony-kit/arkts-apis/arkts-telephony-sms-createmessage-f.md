# createMessage

## 导入模块

```TypeScript
```

## createMessage

```TypeScript
function createMessage(pdu: Array<number>, specification: string, callback: AsyncCallback<ShortMessage>): void
```

根据协议数据单元(PDU)和指定的短信协议创建短信实例。使用callback异步回调。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pdu | Array & lt;number & gt; | 是 | 协议数据单元，从收到的信息中获取。 |
| specification | string | 是 | 短信协议类型。   - 3gpp：表示GSM/UMTS/LTE SMS。   - 3gpp2：表示CDMA SMS。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ShortMessage](arkts-telephony-sms-shortmessage-i.md)&gt; | 是 | 获取短信实例的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

const specification: string = '3gpp';
// 以数组的形式显示协议数据单元(PDU)，类型为number。
const pdu: Array<number> = [0x01, 0x00, 0x05, 0x81, 0x01, 0x80, 0xF6, 0x00, 0x00, 0x05, 0xE8, 0x32, 0x9B, 0xFD, 0x06];
sms.createMessage(pdu, specification, (err: BusinessError, data: sms.ShortMessage) => {
    if (err) {
        console.error('callback: err->${JSON.stringify(err)}');
        return;
    }
    console.info('callback: data->${JSON.stringify(data)}');
});
```


## createMessage

```TypeScript
function createMessage(pdu: Array<number>, specification: string): Promise<ShortMessage>
```

根据协议数据单元(PDU)和指定的短信协议创建短信实例。使用Promise异步回调。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pdu | Array & lt;number & gt; | 是 | 协议数据单元，从收到的信息中获取。 |
| specification | string | 是 | 短信协议类型。   - 3gpp：表示GSM/UMTS/LTE SMS。   - 3gpp2：表示CDMA SMS。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ShortMessage](arkts-telephony-sms-shortmessage-i.md)&gt; | 以Promise形式返回创建的短信实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

const specification: string = '3gpp';
// 以数组的形式显示协议数据单元(PDU)，类型为number。
const pdu: Array<number> = [0x01, 0x00, 0x05, 0x81, 0x01, 0x80, 0xF6, 0x00, 0x00, 0x05, 0xE8, 0x32, 0x9B, 0xFD, 0x06];
sms.createMessage(pdu, specification).then((data: sms.ShortMessage) => {
    console.info(`createMessage success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`createMessage failed, promise: errCode:${err.code},errMsg:${err.message}`);
});
```
