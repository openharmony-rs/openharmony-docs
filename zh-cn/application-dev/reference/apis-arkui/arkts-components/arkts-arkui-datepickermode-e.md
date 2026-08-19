# DatePickerMode

设置日期展示模式。

**起始版本：** 18

<!--Device-unnamed-declare enum DatePickerMode--><!--Device-unnamed-declare enum DatePickerMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

显示年、月、日三列。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerMode-DATE = 0--><!--Device-DatePickerMode-DATE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## YEAR_AND_MONTH

```TypeScript
YEAR_AND_MONTH = 1
```

显示年、月二列。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerMode-YEAR_AND_MONTH = 1--><!--Device-DatePickerMode-YEAR_AND_MONTH = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

显示月、日二列。 在此模式下，年份始终保持不变，取值为selected参数指定的年份。若selected未指定则取当前系统年份。当月份滚动导致日期超出有效范围时， 日期会自动调整至该月最后一天。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-DatePickerMode-MONTH_AND_DAY = 2--><!--Device-DatePickerMode-MONTH_AND_DAY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

