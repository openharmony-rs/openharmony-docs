# isOperatorSimCard（系统接口）

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

<a id="isoperatorsimcard"></a>
## isOperatorSimCard

```TypeScript
function isOperatorSimCard(slotId: number, operator: OperatorSimCard): boolean
```

Indicates whether the SIM card in a specified slot is a specified operator.

**起始版本：** 11

<!--Device-sim-function isOperatorSimCard(slotId: int, operator: OperatorSimCard): boolean--><!--Device-sim-function isOperatorSimCard(slotId: int, operator: OperatorSimCard): boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slot index number supported by the device. |
| operator | [OperatorSimCard](arkts-telephony-sim-operatorsimcard-e-sys.md) | 是 | Indicates the operator of sim. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns {@code true} if the SIM card is specified operator; return {@code false} otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let slotId : number = 0;
let operator : sim.OperatorSimCard = sim.OperatorSimCard.CHINA_TELECOM_CARD;
try {
    let isOperatorSimCard: boolean = sim.isOperatorSimCard(slotId, operator);
    console.info(`is operator sim card: ` + isOperatorSimCard);
} catch (err) {
    console.error("isOperatorSimCard err: " + JSON.stringify(err));
}

```

