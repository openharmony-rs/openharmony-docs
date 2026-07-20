# getOpKeySync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

<a id="getopkeysync"></a>
## getOpKeySync

```TypeScript
function getOpKeySync(slotId: number): string
```

Obtains the operator key of the SIM card in a specified slot.

**起始版本：** 10

<!--Device-sim-function getOpKeySync(slotId: int): string--><!--Device-sim-function getOpKeySync(slotId: int): string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the operator key; returns an empty string if no SIM card is inserted or no operator key is matched. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let data: string = sim.getOpKeySync(0);
console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);

```

