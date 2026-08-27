# getISOCountryCodeForSimSync

## 导入模块

```TypeScript
```

## getISOCountryCodeForSimSync

```TypeScript
function getISOCountryCodeForSimSync(slotId: number): string
```

获取指定卡槽SIM卡的ISO国家码。

**起始版本：** 10

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回获取指定卡槽SIM卡的ISO国家码。例如：CN(中国)。 |

**示例**

```TypeScript
import { sim } from '@kit.TelephonyKit';

let countryCode: string = sim.getISOCountryCodeForSimSync(0);
console.info(`the country ISO is:` + countryCode);
```
