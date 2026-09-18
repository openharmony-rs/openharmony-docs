# getMaxSimCount

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getMaxSimCount

```TypeScript
function getMaxSimCount(): number
```

获取卡槽数量。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 卡槽数量。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

console.info('Result: '+ sim.getMaxSimCount());
```
