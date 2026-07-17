# getSimState

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimState

```TypeScript
function getSimState(slotId: number, callback: AsyncCallback<SimState>): void
```

Obtains the state of the SIM card in a specified slot.

**起始版本：** 6

<!--Device-sim-function getSimState(slotId: int, callback: AsyncCallback<SimState>): void--><!--Device-sim-function getSimState(slotId: int, callback: AsyncCallback<SimState>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from {@code 0} to the maximum card slot index number supported by the device. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<SimState> | 是 | Indicates the callback for getting one of the following SIM card states:&lt;ul&gt;&lt;li&gt;{@code SimState#SIM_STATE_UNKNOWN}&lt;li&gt;{@code SimState#SIM_STATE_NOT_PRESENT}&lt;li&gt;{@code SimState#SIM_STATE_LOCKED}&lt;li&gt;{@code SimState#SIM_STATE_NOT_READY}&lt;li&gt;{@code SimState#SIM_STATE_READY}&lt;li&gt;{@code SimState#SIM_STATE_LOADED}&lt;/ul&gt; |

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

sim.getSimState(0, (err: BusinessError, data: sim.SimState) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});

```


## getSimState

```TypeScript
function getSimState(slotId: number): Promise<SimState>
```

Obtains the state of the SIM card in a specified slot.

**起始版本：** 6

<!--Device-sim-function getSimState(slotId: int): Promise<SimState>--><!--Device-sim-function getSimState(slotId: int): Promise<SimState>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from {@code 0} to the maximum card slot index number supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<SimState> | Returns one of the following SIM card states:&lt;ul&gt;&lt;li&gt;{@code SimState#SIM_STATE_UNKNOWN}&lt;li&gt;{@code SimState#SIM_STATE_NOT_PRESENT}&lt;li&gt;{@code SimState#SIM_STATE_LOCKED}&lt;li&gt;{@code SimState#SIM_STATE_NOT_READY}&lt;li&gt;{@code SimState#SIM_STATE_READY}&lt;li&gt;{@code SimState#SIM_STATE_LOADED}&lt;/ul&gt; |

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

sim.getSimState(0).then((data: sim.SimState) => {
    console.info(`getSimState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimState failed, promise: err->${JSON.stringify(err)}`);
});

```

