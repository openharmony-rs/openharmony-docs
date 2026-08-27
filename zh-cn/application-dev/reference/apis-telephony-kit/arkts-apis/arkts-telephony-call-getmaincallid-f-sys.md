# getMainCallId（系统接口）

## 导入模块

```TypeScript
```

## getMainCallId

```TypeScript
function getMainCallId(callId: number, callback: AsyncCallback<number>): void
```

获取主呼叫Id。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | number | 是 | 呼叫Id。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回主呼叫Id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getMainCallId(1, (err: BusinessError, data: number) => {
    if (err) {
        console.error(`getMainCallId fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`getMainCallId success, data->${JSON.stringify(data)}`);
    }
});
```


## getMainCallId

```TypeScript
function getMainCallId(callId: number): Promise<number>
```

获取主呼叫Id。使用Promise异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | number | 是 | 呼叫Id。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以Promise形式异步返回主呼叫Id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getMainCallId(1).then((data: number) => {
    console.info(`getMainCallId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getMainCallId fail, promise: err->${JSON.stringify(err)}`);
});
```
