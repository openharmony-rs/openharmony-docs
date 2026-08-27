# getSimLabelSync

## 导入模块

```TypeScript
```

## getSimLabelSync

```TypeScript
function getSimLabelSync(slotId: number): SimLabel
```

通过传入SIM卡槽的ID，获取对应的SIM卡标签。

**起始版本：** 20

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SimLabel](arkts-telephony-sim-simlabel-i.md) | SIM卡标签。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';


let simLabel: sim.SimLabel = sim.getSimLabelSync(0);
console.info(`The sim label is:` + simLabel);
```
