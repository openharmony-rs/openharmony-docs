# DatePickerMode

设置日期展示模式。

| 名称 | 值 | 说明 |  
| -------- | - |-------- |  
| DATE | 0 | 显示年、月、日三列。|  
| YEAR_AND_MONTH | 1 | 显示年、月二列。|  
| MONTH_AND_DAY | 2 | 显示月、日二列。

在此模式下，年份始终保持不变。|

**起始版本：** 18

<!--Device-unnamed-declare enum DatePickerMode--><!--Device-unnamed-declare enum DatePickerMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

The date displays three columns: year, month, and day.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerMode-DATE = 0--><!--Device-DatePickerMode-DATE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## YEAR_AND_MONTH

```TypeScript
YEAR_AND_MONTH = 1
```

The date displays two columns: year and month.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerMode-YEAR_AND_MONTH = 1--><!--Device-DatePickerMode-YEAR_AND_MONTH = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

Defines a mode that displays the date in months and days of the month.In this mode, if the month changes from December to January,the year does not increment by one; if the month changes from January to December,the year does not decrement by one. The year remains fixed at the currently set value.

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerMode-MONTH_AND_DAY = 2--><!--Device-DatePickerMode-MONTH_AND_DAY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

