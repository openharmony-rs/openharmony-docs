# getCardTypeSync

## 导入模块

```TypeScript
```

## getCardTypeSync

```TypeScript
function getCardTypeSync(slotId: number): CardType
```

获取指定卡槽SIM卡的卡类型。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| CardType | 返回指定卡槽SIM卡的卡类型。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let cardType: sim.CardType = sim.getCardTypeSync(0);
console.info(`the card type is:` + cardType);
```
