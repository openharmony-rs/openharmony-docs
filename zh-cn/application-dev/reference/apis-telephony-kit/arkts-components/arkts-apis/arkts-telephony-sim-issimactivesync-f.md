# isSimActiveSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## isSimActiveSync

```TypeScript
function isSimActiveSync(slotId: number): boolean
```

获取指定卡槽SIM卡是否激活。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。<br>- 0：卡槽1。<br>- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定卡槽是否激活。<br>- true:激活。<br>- false：未激活。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let isSimActive: boolean = sim.isSimActiveSync(0);
console.info(`the sim is active:` + isSimActive);
```
