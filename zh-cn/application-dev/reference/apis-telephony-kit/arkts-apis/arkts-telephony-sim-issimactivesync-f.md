# isSimActiveSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## isSimActiveSync

```TypeScript
function isSimActiveSync(slotId: int): boolean
```

Checks whether the SIM card in a specified slot is activated.

**起始版本：** 23

<!--Device-sim-function isSimActiveSync(slotId: int): boolean--><!--Device-sim-function isSimActiveSync(slotId: int): boolean-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | Indicates the card slot index number, ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Returns { |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let isSimActive: boolean = sim.isSimActiveSync(0);
console.info(`the sim is active:` + isSimActive);
```

