# hasSimCardSync

## 导入模块

```TypeScript
```

## hasSimCardSync

```TypeScript
function hasSimCardSync(slotId: number): boolean
```

获取指定卡槽SIM卡是否插卡。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定卡槽是否插卡。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let hasSimCard: boolean = sim.hasSimCardSync(0);
console.info(`has sim card: ` + hasSimCard);
```
