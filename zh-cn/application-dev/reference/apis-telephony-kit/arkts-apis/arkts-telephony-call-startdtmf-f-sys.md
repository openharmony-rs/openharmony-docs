# startDTMF（系统接口）

## 导入模块

```TypeScript
```

## startDTMF

```TypeScript
function startDTMF(callId: number, character: string, callback: AsyncCallback<void>): void
```

启动双音多频。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | number | 是 | 呼叫Id。 |
| character | string | 是 | DTMF码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 以回调函数的方式返回启动双音多频的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.startDTMF(1, "0", (err: BusinessError) => {
    if (err) {
        console.error(`startDTMF fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`startDTMF success.`);
    }
});
```


## startDTMF

```TypeScript
function startDTMF(callId: number, character: string): Promise<void>
```

启动双音多频。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callId | number | 是 | 呼叫Id。 |
| character | string | 是 | DTMF码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式异步返回。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.startDTMF(1, "0").then(() => {
    console.info(`startDTMF success.`);
}).catch((err: BusinessError) => {
    console.error(`startDTMF fail, promise: err->${JSON.stringify(err)}`);
});
```
