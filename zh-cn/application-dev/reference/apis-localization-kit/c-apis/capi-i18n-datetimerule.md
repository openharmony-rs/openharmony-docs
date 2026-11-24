# DateTimeRule

```c
typedef struct DateTimeRule {...} DateTimeRule
```

## 概述

时间日期规则。

<!--Device-struct DateTimeRule {...}--><!--Device-struct DateTimeRule {...}-End-->

**系统能力：** SystemCapability.Global.I18n

**起始版本：** 22

**相关模块：** [i18n](capi-localization-kit-i18n.md)

**所在头文件：** [timezone.h](capi-timezone-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t month | 月份。月份从0开始计数，0表示一月。<br><!--Device-int32_t month--><!--Device-int32_t month-End--> |
| int32_t dayOfMonth | 当月的第几天。<br><!--Device-int32_t dayOfMonth--><!--Device-int32_t dayOfMonth-End--> |
| int32_t dayOfWeek | 当周的第几天。<br><!--Device-int32_t dayOfWeek--><!--Device-int32_t dayOfWeek-End--> |
| int32_t weekInMonth | 当月的第几周。<br><!--Device-int32_t weekInMonth--><!--Device-int32_t weekInMonth-End--> |
| int32_t millisInDay | 从当天凌晨0点开始到当前时间的毫秒值。<br><!--Device-int32_t millisInDay--><!--Device-int32_t millisInDay-End--> |
| [DateRuleType](capi-timezone-h.md#dateruletype) dateRuleType | 日期规则类型。<br><!--Device-DateRuleType dateRuleType--><!--Device-DateRuleType dateRuleType-End--> |
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | 时间规则类型。<br><!--Device-TimeRuleType timeRuleType--><!--Device-TimeRuleType timeRuleType-End--> |


