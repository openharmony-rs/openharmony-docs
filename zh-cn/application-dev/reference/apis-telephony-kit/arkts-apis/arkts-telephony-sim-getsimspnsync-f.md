# getSimSpnSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimSpnSync

```TypeScript
function getSimSpnSync(slotId: number): string
```

Obtains the service provider name (SPN) of the SIM card in a specified slot.

<p>The value is recorded in the EFSPN file of the SIM card and is irrelevant to the network with which the SIM card is currently registered.

**起始版本：** 10

<!--Device-sim-function getSimSpnSync(slotId: int): string--><!--Device-sim-function getSimSpnSync(slotId: int): string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the SPN; returns an empty string if no EFSPN file is configured for the SIM card.in the SIM card. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let spn: string = sim.getSimSpnSync(0);
console.info(`the sim card spn is:` + spn);

```

