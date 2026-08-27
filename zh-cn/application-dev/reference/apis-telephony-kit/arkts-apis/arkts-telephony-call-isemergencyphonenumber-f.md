# isEmergencyPhoneNumber

## 导入模块

```TypeScript
```

## isEmergencyPhoneNumber

```TypeScript
function isEmergencyPhoneNumber(phoneNumber: string, options: EmergencyNumberOptions, callback: AsyncCallback<boolean>): void
```

根据电话号码参数，判断是否是紧急电话号码。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [EmergencyNumberOptions](arkts-telephony-call-emergencynumberoptions-i.md) | 是 | 电话号码参数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示是紧急电话号码，返回false表示不是紧急电话号码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: call.EmergencyNumberOptions = {slotId: 1};
call.isEmergencyPhoneNumber("112", options, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isEmergencyPhoneNumber fail, err->Code${err.code}, message:${err.message}`);
    } else {
        console.info(`isEmergencyPhoneNumber success, data->${JSON.stringify(data)}`);
    }
});
```


## isEmergencyPhoneNumber

```TypeScript
function isEmergencyPhoneNumber(phoneNumber: string, options?: EmergencyNumberOptions): Promise<boolean>
```

根据电话号码参数，判断是否是紧急电话号码。使用Promise异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [EmergencyNumberOptions](arkts-telephony-call-emergencynumberoptions-i.md) | 否 | 电话号码参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式异步返回判断是否是紧急电话号码的结果。返回true表示是紧急电话号码，返回false表示不是紧急电话号码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let options: call.EmergencyNumberOptions = {slotId: 1};
call.isEmergencyPhoneNumber("138xxxxxxxx", options).then((data: boolean) => {
    console.info(`isEmergencyPhoneNumber success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isEmergencyPhoneNumber fail, promise: err->Code:${err.code},message:${err.message}`);
});
```


## isEmergencyPhoneNumber

```TypeScript
function isEmergencyPhoneNumber(phoneNumber: string, callback: AsyncCallback<boolean>): void
```

判断是否是紧急电话号码。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示是紧急电话号码，返回false表示不是紧急电话号码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isEmergencyPhoneNumber("138xxxxxxxx", (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isEmergencyPhoneNumber fail, err->Code${err.code}, message:${err.message}`);
    } else {
        console.info(`isEmergencyPhoneNumber success, data->${JSON.stringify(data)}`);
    }
});
```
