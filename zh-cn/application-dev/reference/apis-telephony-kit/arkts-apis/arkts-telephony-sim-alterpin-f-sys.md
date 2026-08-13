# alterPin（系统接口）

## alterPin

```TypeScript
function alterPin(slotId: int, newPin: string, oldPin: string, callback: AsyncCallback<LockStatusResponse>): void
```

Change Pin Password.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function alterPin(slotId: int, newPin: string, oldPin: string, callback: AsyncCallback<LockStatusResponse>): void--><!--Device-sim-function alterPin(slotId: int, newPin: string, oldPin: string, callback: AsyncCallback<LockStatusResponse>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| newPin | string | 是 | Indicates a new password. |
| oldPin | string | 是 | Indicates old password. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md)&gt; | 是 | Indicates the callback for getting the response to obtain the SIM card lock status of the specified card slot. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.alterPin(0, "1234", "0000", (err: BusinessError, data: sim.LockStatusResponse) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## alterPin

```TypeScript
function alterPin(slotId: int, newPin: string, oldPin: string): Promise<LockStatusResponse>
```

Change Pin Password.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.SET_TELEPHONY_STATE

<!--Device-sim-function alterPin(slotId: int, newPin: string, oldPin: string): Promise<LockStatusResponse>--><!--Device-sim-function alterPin(slotId: int, newPin: string, oldPin: string): Promise<LockStatusResponse>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| newPin | string | 是 | Indicates a new password. |
| oldPin | string | 是 | Indicates old password. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md)&gt; | Returns the response to obtain the SIM card lock status of the specified card slot. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.alterPin(0, "1234", "0000").then((data: sim.LockStatusResponse) => {
    console.info(`alterPin success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`alterPin failed, promise: err->${JSON.stringify(err)}`);
});
```

