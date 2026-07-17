# hasSimCardSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## hasSimCardSync

```TypeScript
function hasSimCardSync(slotId: number): boolean
```

Checks whether a SIM card is inserted in a specified slot.

**起始版本：** 10

<!--Device-sim-function hasSimCardSync(slotId: int): boolean--><!--Device-sim-function hasSimCardSync(slotId: int): boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns {@code true} if a SIM card is inserted; return {@code false} otherwise. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let hasSimCard: boolean = sim.hasSimCardSync(0);
console.info(`has sim card: ` + hasSimCard);

```

