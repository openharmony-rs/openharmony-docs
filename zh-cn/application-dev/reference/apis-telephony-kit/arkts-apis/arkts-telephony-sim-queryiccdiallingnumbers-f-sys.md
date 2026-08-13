# queryIccDiallingNumbers（系统接口）

## queryIccDiallingNumbers

```TypeScript
function queryIccDiallingNumbers(slotId: int, type: ContactType, callback: AsyncCallback<Array<DiallingNumbersInfo>>): void
```

Query dialing number information on SIM card.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_CONTACTS

<!--Device-sim-function queryIccDiallingNumbers(slotId: int, type: ContactType, callback: AsyncCallback<Array<DiallingNumbersInfo>>): void--><!--Device-sim-function queryIccDiallingNumbers(slotId: int, type: ContactType, callback: AsyncCallback<Array<DiallingNumbersInfo>>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| type | [ContactType](arkts-telephony-sim-contacttype-e-sys.md) | 是 | Indicates contact type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md)&gt;&gt; | 是 | Indicates the callback for getting the dialing number information. |

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

sim.queryIccDiallingNumbers(0, 1, (err: BusinessError, data: Array<sim.DiallingNumbersInfo>) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## queryIccDiallingNumbers

```TypeScript
function queryIccDiallingNumbers(slotId: int, type: ContactType): Promise<Array<DiallingNumbersInfo>>
```

Query dialing number information on SIM card.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_CONTACTS

<!--Device-sim-function queryIccDiallingNumbers(slotId: int, type: ContactType): Promise<Array<DiallingNumbersInfo>>--><!--Device-sim-function queryIccDiallingNumbers(slotId: int, type: ContactType): Promise<Array<DiallingNumbersInfo>>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| type | [ContactType](arkts-telephony-sim-contacttype-e-sys.md) | 是 | Indicates contact type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[DiallingNumbersInfo](arkts-telephony-sim-diallingnumbersinfo-i-sys.md)&gt;&gt; | Returns the dialing number information. |

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

sim.queryIccDiallingNumbers(0, 1).then((data:  Array<sim.DiallingNumbersInfo>) => {
    console.info(`queryIccDiallingNumbers success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`queryIccDiallingNumbers failed, promise: err->${JSON.stringify(err)}`);
});
```

