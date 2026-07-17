# getISOCountryCodeForSimSync

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getISOCountryCodeForSimSync

```TypeScript
function getISOCountryCodeForSimSync(slotId: number): string
```

Obtains the ISO country code of the SIM card in a specified slot.

**起始版本：** 10

<!--Device-sim-function getISOCountryCodeForSimSync(slotId: int): string--><!--Device-sim-function getISOCountryCodeForSimSync(slotId: int): string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Indicates the card slot index number,ranging from 0 to the maximum card slots supported by the device. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the country code defined in ISO 3166-2; returns an empty string if no SIM card is inserted. |

**示例：**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let countryCode: string = sim.getISOCountryCodeForSimSync(0);
console.info(`the country ISO is:` + countryCode);

```

