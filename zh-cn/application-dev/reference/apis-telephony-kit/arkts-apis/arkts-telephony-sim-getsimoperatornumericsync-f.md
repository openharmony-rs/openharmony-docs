# getSimOperatorNumericSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

<a id="getsimoperatornumericsync"></a>
## getSimOperatorNumericSync

```TypeScript
function getSimOperatorNumericSync(slotId: number): string
```

Obtains the home PLMN number of the SIM card in a specified slot.

<p>The value is recorded in the SIM card and is irrelevant to the network with which the SIM card is currently registered.

**起始版本：** 10

<!--Device-sim-function getSimOperatorNumericSync(slotId: int): string--><!--Device-sim-function getSimOperatorNumericSync(slotId: int): string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the PLMN number; returns an empty string if no SIM card is inserted. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let numeric: string = sim.getSimOperatorNumericSync(0);
console.info(`the sim operator numeric is:` + numeric);

```

