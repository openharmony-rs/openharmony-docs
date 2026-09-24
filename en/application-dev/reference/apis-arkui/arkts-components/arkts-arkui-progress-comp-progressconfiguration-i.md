# ProgressConfiguration

```TypeScript
declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>
```

Provides progress indicator configuration. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total: number
```

Total progress.

Default value: **100**

**NOTE:** 

If the value of **total** is a negative number, it is treated as 100.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Current progress. Values less than 0 are adjusted to **0**. Values greater than the value of **total** are capped at the value of **total**.

Default value: **0**

Value range: [0, total]

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
