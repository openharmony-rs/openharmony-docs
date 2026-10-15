# ProgressConfiguration

```TypeScript
declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>
```

Provides progress indicator configuration. Inherits from [CommonConfiguration](arkts-arkui-common-comp-commonconfiguration-i.md).

**Inheritance/Implementation:** ProgressConfiguration extends CommonConfiguration&lt;ProgressConfiguration&gt;

**Since:** 12

<!--Device-unnamed-declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>--><!--Device-unnamed-declare interface ProgressConfiguration extends CommonConfiguration<ProgressConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total: number
```

Total progress length.

Value range: (0, +∞)

**NOTE:** 

When total is less than or equal to 0, it is handled as 100.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ProgressConfiguration-total: number--><!--Device-ProgressConfiguration-total: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Current progress value. When the set value is less than 0, it is set to 0. When the set value is greater than total, it is set to total.

Default value: 0

Value range: [0, total]

**Note:** When the status of a Ring type progress bar is set to ProgressStatus.LOADING, the set progress value does not take effect.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ProgressConfiguration-value: number--><!--Device-ProgressConfiguration-value: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
