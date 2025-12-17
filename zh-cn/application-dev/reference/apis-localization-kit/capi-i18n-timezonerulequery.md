# TimeZoneRuleQuery

<!--Kit: Localization Kit-->
<!--Subsystem: Global-->
<!--Owner: @yliupy-->
<!--Designer: @sunyaozu-->
<!--Tester: @lpw_work-->
<!--Adviser: @ningningW-->

```c
typedef struct {...} TimeZoneRuleQuery
```

## 概述

用于传入查询的信息，并接收查询的结果。

**起始版本：** 22

**相关模块：** [i18n](capi-i18n.md)

**所在头文件：** [timezone.h](capi-timezone-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double base | 查询的基准时间。 |
| int32_t prevRawOffset | 上一次的时区原始偏移量。 |
| int32_t prevDSTSavings | 上一次的夏令时偏移量。 |
| bool inclusive | 查询结果是否包含基准时间。 |
| double result | 查询结果。 |


