# getDefaultVoiceSimId

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getDefaultVoiceSimId

```TypeScript
function getDefaultVoiceSimId(callback: AsyncCallback<number>): void
```

Obtains the default SIM ID for the voice service.

**起始版本：** 10

<!--Device-sim-function getDefaultVoiceSimId(callback: AsyncCallback<int>): void--><!--Device-sim-function getDefaultVoiceSimId(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | Returns the SIM ID of the default voice sim and SIM ID will increase from 1. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |

**示例：**

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

Obtains the default SIM ID for the voice service.

**起始版本：** 10

<!--Device-sim-function getDefaultVoiceSimId(): Promise<int>--><!--Device-sim-function getDefaultVoiceSimId(): Promise<int>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Returns the SIM ID of the default voice sim and SIM ID will increase from 1. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301001](../errorcode-telephony.md#8301001-sim卡未激活) | SIM card is not activated. |

**示例：**

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

