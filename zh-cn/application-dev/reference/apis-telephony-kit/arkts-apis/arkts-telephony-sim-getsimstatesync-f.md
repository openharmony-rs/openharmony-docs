# getSimStateSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimStateSync

```TypeScript
function getSimStateSync(slotId: number): SimState
```

Obtains the state of the SIM card in a specified slot.

**起始版本：** 10

<!--Device-sim-function getSimStateSync(slotId: int): SimState--><!--Device-sim-function getSimStateSync(slotId: int): SimState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimState](arkts-telephony-sim-simstate-e.md) | Returns one of the following SIM card states:<ul><li>{@code SimState#SIM_STATE_UNKNOWN}<li>{@code SimState#SIM_STATE_NOT_PRESENT}<li>{@code SimState#SIM_STATE_LOCKED}<li>{@code SimState#SIM_STATE_NOT_READY}<li>{@code SimState#SIM_STATE_READY}<li>{@code SimState#SIM_STATE_LOADED}</ul> |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let simState: sim.SimState = sim.getSimStateSync(0);
console.info(`The sim state is:` + simState);

```

