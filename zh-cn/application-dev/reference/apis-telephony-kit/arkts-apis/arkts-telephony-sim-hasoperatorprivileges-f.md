# hasOperatorPrivileges

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## hasOperatorPrivileges

```TypeScript
function hasOperatorPrivileges(slotId: number, callback: AsyncCallback<boolean>): void
```

Checks whether your application (the caller) has been granted the operator permissions.

**起始版本：** 7

<!--Device-sim-function hasOperatorPrivileges(slotId: int, callback: AsyncCallback<boolean>): void--><!--Device-sim-function hasOperatorPrivileges(slotId: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from {@code 0} to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | Indicates the callback of hasOperatorPrivileges.Returns {@code true} if your application has been granted the operator permissions; returns {@code false} otherwise.If no SIM card is inserted or the SIM card is deactivated will be return {@code false}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasOperatorPrivileges(0, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

```


## hasOperatorPrivileges

```TypeScript
function hasOperatorPrivileges(slotId: number): Promise<boolean>
```

Checks whether your application (the caller) has been granted the operator permissions.

**起始版本：** 7

<!--Device-sim-function hasOperatorPrivileges(slotId: int): Promise<boolean>--><!--Device-sim-function hasOperatorPrivileges(slotId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from {@code 0} to the maximum card slot index number supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Returns {@code true} if your application has been granted the operator permissions;returns {@code false} otherwise. If no SIM card is inserted or the SIM card is deactivated will be return {@code false}. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.hasOperatorPrivileges(0).then((data: boolean) => {
    console.info(`hasOperatorPrivileges success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`hasOperatorPrivileges failed, promise: err->${JSON.stringify(err)}`);
});

```

