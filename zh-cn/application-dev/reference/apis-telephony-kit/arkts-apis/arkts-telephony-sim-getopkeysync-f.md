# getOpKeySync

## 导入模块

```TypeScript
```

## getOpKeySync

```TypeScript
function getOpKeySync(slotId: number): string
```

获取指定卡槽中SIM卡的opkey。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定卡槽中SIM卡的opkey。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let data: string = sim.getOpKeySync(0);
console.info(`getOpKey success, promise: data->${JSON.stringify(data)}`);
```
