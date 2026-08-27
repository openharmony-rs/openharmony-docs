# getISOCountryCodeForNetwork

## 导入模块

```TypeScript
```

## getISOCountryCodeForNetwork

```TypeScript
function getISOCountryCodeForNetwork(slotId: number, callback: AsyncCallback<string>): void
```

获取注册网络所在国家的ISO国家码。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数。返回国家码，例如：CN(中国)。如果设备没有注册任何网络，接口返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getISOCountryCodeForNetwork(slotId, (err: BusinessError, data: string) => {
    if (err) {
        console.error(`getISOCountryCodeForNetwork failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getISOCountryCodeForNetwork success, callback: data->${JSON.stringify(data)}`);
});
```


## getISOCountryCodeForNetwork

```TypeScript
function getISOCountryCodeForNetwork(slotId: number): Promise<string>
```

获取注册网络所在国家的ISO国家码。使用Promise异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | 以Promise形式返回注册网络所在国家的ISO国家码，例如CN(中国)。如果设备没有注册任何网络，接口返回空字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getISOCountryCodeForNetwork(slotId).then((data: string) => {
    console.info(`getISOCountryCodeForNetwork success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getISOCountryCodeForNetwork failed, promise: err->${JSON.stringify(err)}`);
});
```
