# TimeArrayTimeZoneRule

```c
typedef struct TimeArrayTimeZoneRule {...} TimeArrayTimeZoneRule
```

## 概述

起始时间戳数组定义的时区规则。

<!--Device-struct TimeArrayTimeZoneRule {...}--><!--Device-struct TimeArrayTimeZoneRule {...}-End-->

**系统能力：** SystemCapability.Global.I18n

**起始版本：** 22

**相关模块：** [i18n](capi-localization-kit-i18n.md)

**所在头文件：** [timezone.h](capi-timezone-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* name | 时区规则的名称。<br><!--Device-char* name--><!--Device-char* name-End--> |
| int32_t rawOffset | 时区的原始偏移量，单位为毫秒（ms）。<br><!--Device-int32_t rawOffset--><!--Device-int32_t rawOffset-End--> |
| int32_t dstSavings | 夏令时的偏移量，单位为毫秒（ms）。<br><!--Device-int32_t dstSavings--><!--Device-int32_t dstSavings-End--> |
| double* startTimes | 规则生效的起始时间戳数组，起始时间戳单位为毫秒（ms）。<br><!--Device-double* startTimes--><!--Device-double* startTimes-End--> |
| int32_t numStartTimes | 规则生效的起始时间戳数组的大小。<br><!--Device-int32_t numStartTimes--><!--Device-int32_t numStartTimes-End--> |
| [TimeRuleType](capi-timezone-h.md#timeruletype) timeRuleType | 时间规则类型。<br><!--Device-TimeRuleType timeRuleType--><!--Device-TimeRuleType timeRuleType-End--> |


