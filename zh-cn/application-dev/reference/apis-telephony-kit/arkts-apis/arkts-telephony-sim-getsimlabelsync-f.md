# getSimLabelSync

## getSimLabelSync

```TypeScript
function getSimLabelSync(slotId: int): SimLabel
```

Obtains the SIM card label synchronously.

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为23。

<!--Device-sim-function getSimLabelSync(slotId: int): SimLabel--><!--Device-sim-function getSimLabelSync(slotId: int): SimLabel-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | SIM card slot ID, which ranges from 0 to the maximum number of slots supported |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | SIM card label. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';


let simLabel: sim.SimLabel = sim.getSimLabelSync(0);
console.info(`The sim state is:` + simLabel);
```

