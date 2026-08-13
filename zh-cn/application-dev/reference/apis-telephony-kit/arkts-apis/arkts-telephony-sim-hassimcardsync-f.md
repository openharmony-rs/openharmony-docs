# hasSimCardSync

## hasSimCardSync

```TypeScript
function hasSimCardSync(slotId: int): boolean
```

Checks whether a SIM card is inserted in a specified slot.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sim-function hasSimCardSync(slotId: int): boolean--><!--Device-sim-function hasSimCardSync(slotId: int): boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns { |

## 示例

```TypeScript
import { sim } from '@kit.TelephonyKit';

let hasSimCard: boolean = sim.hasSimCardSync(0);
console.info(`has sim card: ` + hasSimCard);
```

