# isRadioOn

## 导入模块

```TypeScript
```

## isRadioOn

```TypeScript
function isRadioOn(slotId: number, callback: AsyncCallback<boolean>): void
```

判断指定卡槽位的Radio是否打开。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回指定卡槽的Radio状态。   - true：Radio打开。   - false：Radio关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.isRadioOn(slotId, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isRadioOn failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`isRadioOn success, callback: data->${JSON.stringify(data)}`);
});
```


## isRadioOn

```TypeScript
function isRadioOn(slotId?: number): Promise<boolean>
```

判断Radio是否打开。使用Promise异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 否 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。   如果不指定slotId，默认判断主卡Radio是否打开 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回判断Radio是否打开的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.isRadioOn(slotId).then((data: boolean) => {
    console.info(`isRadioOn success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isRadioOn failed, promise: err->${JSON.stringify(err)}`);
});
```


## isRadioOn

```TypeScript
function isRadioOn(callback: AsyncCallback<boolean>): void
```

判断主卡的Radio是否打开。使用callback异步回调。

**起始版本：** 7

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。返回主卡的Radio状态。   - true：Radio打开。   - false：Radio关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

radio.isRadioOn((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isRadioOn failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`isRadioOn success, callback: data->${JSON.stringify(data)}`);
});
```
