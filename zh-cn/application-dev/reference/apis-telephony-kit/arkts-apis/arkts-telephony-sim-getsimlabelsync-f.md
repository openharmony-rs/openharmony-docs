# getSimLabelSync

## getSimLabelSync

```TypeScript
function getSimLabelSync(slotId: int): SimLabel
```

Obtains the SIM card label synchronously.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sim-function getSimLabelSync(slotId: int): SimLabel--><!--Device-sim-function getSimLabelSync(slotId: int): SimLabel-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | SIM card slot ID, which ranges from 0 to the maximum number of slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimLabel](arkts-telephony-sim-simlabel-i.md) | SIM card label. |

## 示例

```TypeScript
import { sim } from '@kit.TelephonyKit';


let simLabel: sim.SimLabel = sim.getSimLabelSync(0);
console.info(`The sim state is:` + simLabel);
```

