# getMaxSimCount

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getMaxSimCount

```TypeScript
function getMaxSimCount(): int
```

Obtains the maximum number of SIM cards that can be used simultaneously on the device, that is, the maximum number of SIM card slots.

**起始版本：** 23

<!--Device-sim-function getMaxSimCount(): int--><!--Device-sim-function getMaxSimCount(): int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | Returns the maximum number of SIM card slots. |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

console.info("Result: "+ sim.getMaxSimCount());
```

