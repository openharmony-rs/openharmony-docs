# rejectCall（系统接口）

## rejectCall

```TypeScript
function rejectCall(callId: int, options: RejectMessageOptions, callback: AsyncCallback<void>): void
```

拒绝来电。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ANSWER_CALL

<!--Device-call-function rejectCall(callId: int, options: RejectMessageOptions, callback: AsyncCallback<void>): void--><!--Device-call-function rejectCall(callId: int, options: RejectMessageOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。可以通过订阅callDetailsChange事件获得。 |
| options | [RejectMessageOptions](arkts-telephony-call-rejectmessageoptions-i-sys.md) | 是 | 拒绝消息选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以回调函数的方式返回拒接电话的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rejectMessageOptions : call.RejectMessageOptions = {
    messageContent: "拦截陌生号码"
}
call.rejectCall(1, rejectMessageOptions, (err: BusinessError) => {
    if (err) {
        console.error(`rejectCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`rejectCall success.`);
    }
});
```


## rejectCall

```TypeScript
function rejectCall(callId?: int, options?: RejectMessageOptions): Promise<void>
```

拒绝来电。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ANSWER_CALL

<!--Device-call-function rejectCall(callId?: int, options?: RejectMessageOptions): Promise<void>--><!--Device-call-function rejectCall(callId?: int, options?: RejectMessageOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 否 | 呼叫Id。可以通过订阅callDetailsChange事件获得。从API version 9开始为可选参数。&lt;br/&gt;不填该参数则拒接最近一通正在响铃的来电。 |
| options | [RejectMessageOptions](arkts-telephony-call-rejectmessageoptions-i-sys.md) | 否 | 拒绝消息选项。不填该参数则不会发送拒接短信。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rejectMessageOptions: call.RejectMessageOptions = {
    messageContent: "拦截陌生号码"
}
call.rejectCall(1, rejectMessageOptions).then(() => {
    console.info(`rejectCall success.`);
}).catch((err: BusinessError) => {
    console.error(`rejectCall fail, promise: err->${JSON.stringify(err)}`);
});
```


## rejectCall

```TypeScript
function rejectCall(callId: int, callback: AsyncCallback<void>): void
```

拒绝来电。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ANSWER_CALL

<!--Device-call-function rejectCall(callId: int, callback: AsyncCallback<void>): void--><!--Device-call-function rejectCall(callId: int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。可以通过订阅callDetailsChange事件获得。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以回调函数的方式返回拒接电话的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.rejectCall(1, (err: BusinessError) => {
    if (err) {
        console.error(`rejectCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`rejectCall success.`);
    }
});
```


## rejectCall

```TypeScript
function rejectCall(callback: AsyncCallback<void>): void
```

拒绝来电。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ANSWER_CALL or ohos.permission.MANAGE_CALL_FOR_DEVICES

<!--Device-call-function rejectCall(callback: AsyncCallback<void>): void--><!--Device-call-function rejectCall(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当拒接来电成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs.<br>**适用版本：** 9 - 22 |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.rejectCall((err: BusinessError) => {
    if (err) {
        console.error(`rejectCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`rejectCall success.`);
    }
});
```


## rejectCall

```TypeScript
function rejectCall(options: RejectMessageOptions, callback: AsyncCallback<void>): void
```

拒绝来电。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ANSWER_CALL

<!--Device-call-function rejectCall(options: RejectMessageOptions, callback: AsyncCallback<void>): void--><!--Device-call-function rejectCall(options: RejectMessageOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RejectMessageOptions](arkts-telephony-call-rejectmessageoptions-i-sys.md) | 是 | 拒绝消息选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以回调函数的方式返回拒接电话的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rejectMessageOptions: call.RejectMessageOptions = {
    messageContent: "拦截陌生号码"
}
call.rejectCall(rejectMessageOptions, (err: BusinessError) => {
    if (err) {
        console.error(`rejectCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`rejectCall success.`);
    }
});
```

