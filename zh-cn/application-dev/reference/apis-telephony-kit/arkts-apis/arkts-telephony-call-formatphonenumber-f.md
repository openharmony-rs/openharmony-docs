# formatPhoneNumber

## 导入模块

```TypeScript
```

## formatPhoneNumber

```TypeScript
function formatPhoneNumber(phoneNumber: string, options: NumberFormatOptions, callback: AsyncCallback<string>): void
```

格式化电话号码，可设置格式化参数。使用callback异步回调。电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [NumberFormatOptions](arkts-telephony-call-numberformatoptions-i.md) | 是 | 格式化参数，如国家码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回格式化电话号码的结果。 |

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

let options: call.NumberFormatOptions = {
    countryCode: "CN"
};
call.formatPhoneNumber("138xxxxxxxx", options, (err: BusinessError, data: string) => {
    if (err) {
        console.error(`formatPhoneNumber fail, err->Code${err.code}, message:${err.message}`);
    } else {
        console.info(`formatPhoneNumber success, data->${JSON.stringify(data)}`);
    }
});
```


## formatPhoneNumber

```TypeScript
function formatPhoneNumber(phoneNumber: string, options?: NumberFormatOptions): Promise<string>
```

格式化电话号码，可设置格式化参数。使用Promise异步回调。电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [NumberFormatOptions](arkts-telephony-call-numberformatoptions-i.md) | 否 | 格式化参数，如国家码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | 以Promise形式异步返回格式化电话号码的结果。 |

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

let options: call.NumberFormatOptions = {
    countryCode: "CN"
};
call.formatPhoneNumber("138xxxxxxxx", options).then((data: string) => {
    console.info(`formatPhoneNumber success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`formatPhoneNumber fail, promise: err->Code${err.code}, message:${err.message}`);
});
```


## formatPhoneNumber

```TypeScript
function formatPhoneNumber(phoneNumber: string, callback: AsyncCallback<string>): void
```

格式化电话号码。使用callback异步回调。电话号码格式化后为标准数字字符串，例如：“138 xxxx xxxx”、“0755 xxxx xxxx”。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回格式化电话号码的结果。 |

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

call.formatPhoneNumber("138xxxxxxxx", (err: BusinessError, data: string) => {
    if (err) {
        console.error(`formatPhoneNumber fail, err->Code${err.code}, message:${err.message}`);
    } else {
        console.info(`formatPhoneNumber success, data->${JSON.stringify(data)}`);
    }
});
```
