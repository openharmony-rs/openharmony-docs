# sendShortMessage

## 导入模块

```TypeScript
```

## sendShortMessage

```TypeScript
function sendShortMessage(options: SendMessageOptions, callback: AsyncCallback<void>): void
```

发送短信。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md) | 是 | 发送短信的参数和回调，参考[SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 发送短信的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let sendCallback: AsyncCallback<sms.ISendShortMessageCallback> = (err: BusinessError, data: sms.ISendShortMessageCallback) => {
    if (err) {
        console.error('sendCallback: err->${JSON.stringify(err)}');
        return;
    }
    console.info('sendCallback: data->${JSON.stringify(data)}');
};
let deliveryCallback: AsyncCallback<sms.IDeliveryShortMessageCallback> = (err: BusinessError, data: sms.IDeliveryShortMessageCallback) => {
    if (err) {
        console.error('deliveryCallback: err->${JSON.stringify(err)}');
        return;
    }
    console.info('deliveryCallback: data->${JSON.stringify(data)}');
};
let options: sms.SendMessageOptions = {
    slotId: 0,
    content: '短信内容',
    destinationHost: '+861xxxxxxxxxx',
    serviceCenter: '+861xxxxxxxxxx',
    destinationPort: 1000,
    sendCallback: sendCallback,
    deliveryCallback: deliveryCallback
};
sms.sendShortMessage(options, (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## sendShortMessage

```TypeScript
function sendShortMessage(options: SendMessageOptions): Promise<void>
```

发送短信。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.SEND_MESSAGES

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md) | 是 | 发送短信的参数和回调，参考[SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式返回发送短信的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let sendCallback: AsyncCallback<sms.ISendShortMessageCallback> = (err: BusinessError, data: sms.ISendShortMessageCallback) => {
    if (err) {
        console.error('sendCallback: err->${JSON.stringify(err)}');
        return;
    }
    console.info('sendCallback: data->${JSON.stringify(data)}');
};
let deliveryCallback: AsyncCallback<sms.IDeliveryShortMessageCallback> = (err: BusinessError, data: sms.IDeliveryShortMessageCallback) => {
    if (err) {
        console.error('deliveryCallback: err->${JSON.stringify(err)}');
        return;
    }
    console.info('deliveryCallback: data->${JSON.stringify(data)}');
};
let options: sms.SendMessageOptions = {
    slotId: 0,
    content: '短信内容',
    destinationHost: '+861xxxxxxxxxx',
    serviceCenter: '+861xxxxxxxxxx',
    destinationPort: 1000,
    sendCallback: sendCallback,
    deliveryCallback: deliveryCallback
};
let promise = sms.sendShortMessage(options);
promise.then(() => {
    console.info(`sendShortMessage success`);
}).catch((err: BusinessError) => {
    console.error(`sendShortMessage failed, promise: errCode:${err.code},errMsg:${err.message}`);
});
```
