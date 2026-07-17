# unlockPuk（系统接口）

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## unlockPuk

```TypeScript
function unlockPuk(slotId: number, newPin: string, puk: string, callback: AsyncCallback<LockStatusResponse>): void
```

Unlock the SIM card password in the specified card slot.

**起始版本：** 7

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function unlockPuk(slotId: int, newPin: string, puk: string, callback: AsyncCallback<LockStatusResponse>): void--><!--Device-sim-function unlockPuk(slotId: int, newPin: string, puk: string, callback: AsyncCallback<LockStatusResponse>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slot index number supported by the device. |
| newPin | string | 是 | Indicates to reset the SIM card password. |
| puk | string | 是 | Indicates the unlock password of the SIM card password. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<LockStatusResponse> | 是 | Indicates the callback for getting the response to obtain the SIM card lock status of the specified card slot. |

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
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let puk: string = '1xxxxxxx';
let newPin: string = '1235';
sim.unlockPuk(0, newPin, puk, (err: BusinessError, data: sim.LockStatusResponse) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

```


## unlockPuk

```TypeScript
function unlockPuk(slotId: number, newPin: string, puk: string): Promise<LockStatusResponse>
```

Unlock the SIM card password in the specified card slot.

**起始版本：** 7

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function unlockPuk(slotId: int, newPin: string, puk: string): Promise<LockStatusResponse>--><!--Device-sim-function unlockPuk(slotId: int, newPin: string, puk: string): Promise<LockStatusResponse>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slot index number supported by the device. |
| newPin | string | 是 | Indicates to reset the SIM card password. |
| puk | string | 是 | Indicates the unlock password of the SIM card password. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<LockStatusResponse> | Returns the response to obtain the SIM card lock status of the specified card slot. |

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
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let puk: string = '1xxxxxxx';
let newPin: string = '1235';
sim.unlockPuk(0, newPin, puk).then((data: sim.LockStatusResponse) => {
    console.info(`unlockPuk success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`unlockPuk failed, promise: err->${JSON.stringify(err)}`);
});

```

