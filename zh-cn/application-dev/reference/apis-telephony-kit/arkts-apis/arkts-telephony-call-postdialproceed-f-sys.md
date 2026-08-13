# postDialProceed（系统接口）

## postDialProceed

```TypeScript
function postDialProceed(callId: int, proceed: boolean, callback: AsyncCallback<void>): void
```

继续进行通话。使用callback异步回调。 当用户呼叫号码为：“普通电话号码”+“;”+"DTMF字符"(例如：“400xxxxxxx;123”)，并且已经订阅了通话后延迟事件，电话接通后，系统将上报通话后延迟事件，应用可以调用此接口选择是否发送DTMF音。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-call-function postDialProceed(callId: int, proceed: boolean, callback: AsyncCallback<void>): void--><!--Device-call-function postDialProceed(callId: int, proceed: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。 |
| proceed | boolean | 是 | 用户选择是否发送DTMF(Dual Tone Multi Frequency，双音多频)音，默认为false。&lt;br/&gt;-true：是&lt;br/&gt;-false：否 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以回调函数的方式返回继续进行通话的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.postDialProceed(1, true, (err: BusinessError) => {
    console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## postDialProceed

```TypeScript
function postDialProceed(callId: int, proceed: boolean): Promise<void>
```

继续进行通话。使用Promise异步回调。 当用户呼叫号码为：“普通电话号码”+“;”+"DTMF字符"(例如：“400xxxxxxx;123”)，并且已经订阅了通话后延迟事件，电话接通后，系统将上报通话后延迟事件，应用可以调用此接口选择是否发送DTMF音。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-call-function postDialProceed(callId: int, proceed: boolean): Promise<void>--><!--Device-call-function postDialProceed(callId: int, proceed: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。 |
| proceed | boolean | 是 | 用户选择是否发送DTMF音，默认为false。&lt;br/&gt;-true：是&lt;br/&gt;-false：否 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.postDialProceed(1, true).then(() => {
    console.info(`postDialProceed success.`);
}).catch((err: BusinessError) => {
    console.error(`postDialProceed fail, promise: err->${JSON.stringify(err)}`);
});
```

