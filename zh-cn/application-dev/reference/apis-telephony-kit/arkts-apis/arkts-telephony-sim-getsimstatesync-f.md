# getSimStateSync

## getSimStateSync

```TypeScript
function getSimStateSync(slotId: int): SimState
```

Obtains the state of the SIM card in a specified slot.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sim-function getSimStateSync(slotId: int): SimState--><!--Device-sim-function getSimStateSync(slotId: int): SimState-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimState | Returns one of the following SIM card states: &lt;ul&gt; &lt;li&gt;{ |

## 示例

```TypeScript
import { sim } from '@kit.TelephonyKit';

let simState: sim.SimState = sim.getSimStateSync(0);
console.info(`The sim state is:` + simState);
```

