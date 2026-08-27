# ZoneRules

提供查询时区跳变规则的能力。

**起始版本：** 20

**系统能力：** SystemCapability.Global.I18n

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## nextTransition

```TypeScript
public nextTransition(date?: number): ZoneOffsetTransition
```

获取指定时间的下一个时区跳变对象。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.I18n

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| date | number | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ZoneOffsetTransition](arkts-localization-i18n-zoneoffsettransition-c.md) | 时区跳变对象。 |

**示例**

```TypeScript
import { i18n } from '@kit.LocalizationKit';

// 获取蒂华纳时区对象
let timeZone: i18n.TimeZone = i18n.getTimeZone('America/Tijuana');
// 获取蒂华纳时区跳变规则
let zoneRules: i18n.ZoneRules = timeZone.getZoneRules();
let date = new Date(2025, 4, 13);
// 获取蒂华纳时区2025年5月13日后的下一个跳变对象
let zoneOffsetTransition: i18n.ZoneOffsetTransition = zoneRules.nextTransition(date.getTime());
```
