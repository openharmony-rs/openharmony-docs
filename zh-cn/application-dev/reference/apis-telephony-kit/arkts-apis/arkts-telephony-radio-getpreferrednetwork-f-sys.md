# getPreferredNetwork（系统接口）

## 导入模块

```TypeScript
```

## getPreferredNetwork

```TypeScript
function getPreferredNetwork(slotId: number, callback: AsyncCallback<PreferredNetworkMode>): void
```

Get the preferred network for the specified SIM card slot.

**起始版本：** 8

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PreferredNetworkMode](arkts-telephony-radio-preferrednetworkmode-e-sys.md)&gt; | 是 | Indicates the callback for getting the preferred network mode to obtain. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getPreferredNetwork(slotId, (err: BusinessError, data: radio.PreferredNetworkMode) => {
    if (err) {
        console.error(`getPreferredNetwork failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getPreferredNetwork success, callback: data->${JSON.stringify(data)}`);
});
```


## getPreferredNetwork

```TypeScript
function getPreferredNetwork(slotId: number): Promise<PreferredNetworkMode>
```

Get the preferred network for the specified SIM card slot.

**起始版本：** 8

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PreferredNetworkMode](arkts-telephony-radio-preferrednetworkmode-e-sys.md)&gt; | Returns the callback for getting the preferred network mode to obtain. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getPreferredNetwork(slotId).then((data: radio.PreferredNetworkMode) => {
    console.info(`getPreferredNetwork success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getPreferredNetwork failed, promise: err->${JSON.stringify(err)}`);
});
```
