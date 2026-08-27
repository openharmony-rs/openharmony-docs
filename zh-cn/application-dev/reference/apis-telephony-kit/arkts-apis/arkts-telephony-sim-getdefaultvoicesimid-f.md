# getDefaultVoiceSimId

## 导入模块

```TypeScript
```

## getDefaultVoiceSimId

```TypeScript
function getDefaultVoiceSimId(callback: AsyncCallback<number>): void
```

获取默认语音业务的SIM卡ID。使用callback异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。与SIM卡绑定，从1开始递增。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDefaultVoiceSimId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getDefaultVoiceSimId

```TypeScript
function getDefaultVoiceSimId(): Promise<number>
```

获取默认语音业务的SIM卡ID。使用Promise异步回调。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以Promise形式返回默认语音业务的SIM卡ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let promise = sim.getDefaultVoiceSimId();
promise.then((data: number) => {
    console.info(`getDefaultVoiceSimId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultVoiceSimId failed, promise: err->${JSON.stringify(err)}`);
});
```
