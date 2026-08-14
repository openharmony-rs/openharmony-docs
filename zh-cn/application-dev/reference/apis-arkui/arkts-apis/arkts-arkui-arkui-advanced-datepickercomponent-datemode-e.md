# DateMode

DateMode枚举用于定义日期选择器的模式。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare enum DateMode--><!--Device-unnamed-export declare enum DateMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DATE

```TypeScript
DATE = 0
```

日期显示三列：年、月、日。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateMode-YEAR_AND_MONTH = 1--><!--Device-DateMode-YEAR_AND_MONTH = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MONTH_AND_DAY

```TypeScript
MONTH_AND_DAY = 2
```

显示月、日二列。在此模式下，年份始终保持不变，取值为selected指定的年份；若selected未指定则取当前系统年份。当月份从12月变为1月时， 年份不会增加；当月份从1月变为12月时，年份不会减少。当月份滚动导致日期超出有效范围时，日期会自动调整至该月最后一天。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-DateMode-MONTH_AND_DAY = 2--><!--Device-DateMode-MONTH_AND_DAY = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

