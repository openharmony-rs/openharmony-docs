# getSimAccountInfo

## getSimAccountInfo

```TypeScript
function getSimAccountInfo(slotId: int, callback: AsyncCallback<IccAccountInfo>): void
```

Get account information of SIM card.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getSimAccountInfo(slotId: int, callback: AsyncCallback<IccAccountInfo>): void--><!--Device-sim-function getSimAccountInfo(slotId: int, callback: AsyncCallback<IccAccountInfo>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt; | 是 | Indicates the callback for getting a {@code IccAccountInfo} object. The ICCID and phone number will be null if the permission ohos.permission.GET_TELEPHONY_STATE is not granted. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAccountInfo(0, (err:BusinessError , data: sim.IccAccountInfo) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getSimAccountInfo

```TypeScript
function getSimAccountInfo(slotId: int): Promise<IccAccountInfo>
```

Get account information of SIM card.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getSimAccountInfo(slotId: int): Promise<IccAccountInfo>--><!--Device-sim-function getSimAccountInfo(slotId: int): Promise<IccAccountInfo>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt; | Returns a { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | The SIM card failed to read or update data. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAccountInfo(0).then((data: sim.IccAccountInfo) => {
    console.info(`getSimAccountInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimAccountInfo failed, promise: err->${JSON.stringify(err)}`);
});
```

