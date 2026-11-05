# isOperatorSimCard（系统接口）

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## isOperatorSimCard

```TypeScript
function isOperatorSimCard(slotId: number, operator: OperatorSimCard): boolean
```

获取指定卡槽SIM卡是否为指定运营商卡。例如，运营商专属应用在启动时可通过此接口判断当前SIM卡是否为自家运营商卡，从而决定是否展示运营商专属服务或功能。

**起始版本：** 11

<!--Device-sim-function isOperatorSimCard(slotId: int, operator: OperatorSimCard): boolean--><!--Device-sim-function isOperatorSimCard(slotId: int, operator: OperatorSimCard): boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1<br>- 1：卡槽2。<br>取值限定为整数。 |
| operator | [OperatorSimCard](arkts-telephony-sim-operatorsimcard-e-sys.md) | 是 | 运营商卡名称。（当前仅支持中国电信卡）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定卡槽是否为指定运营商卡<br>- true：是<br>- false：否 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-函数参数数量或参数类型不匹配) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.         2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

<!--Del-->
**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let slotId : number = 0;
let operator : sim.OperatorSimCard = sim.OperatorSimCard.CHINA_TELECOM_CARD;
try {
    let isOperatorSimCard: boolean = sim.isOperatorSimCard(slotId, operator);
    console.info(`is operator sim card: ` + isOperatorSimCard);
} catch (err) {
    console.error('isOperatorSimCard err: ' + JSON.stringify(err));
}
```

<!--DelEnd-->
