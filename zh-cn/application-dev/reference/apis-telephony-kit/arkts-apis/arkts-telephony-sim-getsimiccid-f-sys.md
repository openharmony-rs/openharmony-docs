# getSimIccId（系统接口）

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimIccId

```TypeScript
function getSimIccId(slotId: number, callback: AsyncCallback<string>): void
```

Obtains the ICCID of the SIM card in a specified slot.

<p>The ICCID is a unique identifier of a SIM card. It consists of 20 digits and is recorded in the EFICCID file of the SIM card.

**起始版本：** 7

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getSimIccId(slotId: int, callback: AsyncCallback<string>): void--><!--Device-sim-function getSimIccId(slotId: int, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string> | 是 | Indicates the callback for getting the ICCID;returns an empty string if no SIM card is inserted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimIccId(0, (err: BusinessError, data: string) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

```


## getSimIccId

```TypeScript
function getSimIccId(slotId: number): Promise<string>
```

Obtains the ICCID of the SIM card in a specified slot.

<p>The ICCID is a unique identifier of a SIM card. It consists of 20 digits and is recorded in the EFICCID file of the SIM card.

**起始版本：** 7

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getSimIccId(slotId: int): Promise<string>--><!--Device-sim-function getSimIccId(slotId: int): Promise<string>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slot index number supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string> | Returns the ICCID; returns an empty string if no SIM card is inserted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimIccId(0).then((data:string) => {
    console.info(`getSimIccId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimIccId failed, promise: err->${JSON.stringify(err)}`);
});

```

