# getMaxSimCount

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

<a id="getmaxsimcount"></a>
## getMaxSimCount

```TypeScript
function getMaxSimCount(): number
```

Obtains the maximum number of SIM cards that can be used simultaneously on the device,that is, the maximum number of SIM card slots.

**起始版本：** 7

<!--Device-sim-function getMaxSimCount(): int--><!--Device-sim-function getMaxSimCount(): int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Returns the maximum number of SIM card slots. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

console.info("Result: "+ sim.getMaxSimCount());

```

