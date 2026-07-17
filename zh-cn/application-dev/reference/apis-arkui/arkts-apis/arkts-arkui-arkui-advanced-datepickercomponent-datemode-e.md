# DateMode

DateMode枚举用于定义日期选择器的模式。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare enum DateMode--><!--Device-unnamed-export declare enum DateMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

日期显示三列：年、月、日。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateMode-DATE = 0--><!--Device-DateMode-DATE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## YEAR_AND_MONTH

```TypeScript
YEAR_AND_MONTH = 1
```

日期显示两列：年、月。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateMode-YEAR_AND_MONTH = 1--><!--Device-DateMode-YEAR_AND_MONTH = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

定义以月和日显示日期的模式。在此模式下，当月份从12月变为1月时，年份不会增加；当月份从1月变为12月时，年份不会减少。年份保持当前设置的值不变。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateMode-MONTH_AND_DAY = 2--><!--Device-DateMode-MONTH_AND_DAY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

