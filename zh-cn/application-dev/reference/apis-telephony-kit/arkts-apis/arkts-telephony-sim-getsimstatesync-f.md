# getSimStateSync

## 导入模块

```TypeScript
```

## getSimStateSync

```TypeScript
function getSimStateSync(slotId: number): SimState
```

获取指定卡槽的SIM卡状态。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SimState | 返回获取指定卡槽的SIM卡状态。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let simState: sim.SimState = sim.getSimStateSync(0);
console.info(`The sim state is:` + simState);
```
