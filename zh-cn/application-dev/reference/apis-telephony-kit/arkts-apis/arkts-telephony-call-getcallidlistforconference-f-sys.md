# getCallIdListForConference（系统接口）

## getCallIdListForConference

```TypeScript
function getCallIdListForConference(callId: int, callback: AsyncCallback<Array<string>>): void
```

获取会议的呼叫Id列表。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function getCallIdListForConference(callId: int, callback: AsyncCallback<Array<string>>): void--><!--Device-call-function getCallIdListForConference(callId: int, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。返回会议的呼叫Id列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallIdListForConference(1, (err: BusinessError, data: Array<string>) => {
    if (err) {
        console.error(`getCallIdListForConference fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`getCallIdListForConference success, data->${JSON.stringify(data)}`);
    }
});
```


## getCallIdListForConference

```TypeScript
function getCallIdListForConference(callId: int): Promise<Array<string>>
```

获取会议的呼叫Id列表。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function getCallIdListForConference(callId: int): Promise<Array<string>>--><!--Device-call-function getCallIdListForConference(callId: int): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | int | 是 | 呼叫Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | 以Promise形式异步返回会议的呼叫Id列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallIdListForConference(1).then((data: Array<string>) => {
    console.info(`getCallIdListForConference success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCallIdListForConference fail, promise: err->${JSON.stringify(err)}`);
});
```

