# ProgressOptions

```TypeScript
declare interface ProgressOptions<Type extends keyof ProgressStyleMap>
```

Defines progress bar options.

**Since:** 7

<!--Device-unnamed-declare interface ProgressOptions<Type extends keyof ProgressStyleMap>--><!--Device-unnamed-declare interface ProgressOptions<Type extends keyof ProgressStyleMap>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total?: number
```

Specifies the total length of the progress. When the value is set less than 0, it is set to 100.

Default value: **100**

Value range: (0, +∞).

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressOptions-total?: number--><!--Device-ProgressOptions-total?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: Type
```

Specifies the progress bar type. Type inherits from [ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md).

Default value: **ProgressType.Linear**

**Note:** Different [ProgressType](arkts-arkui-progress-comp-progresstype-e.md) values must correspond to the respective [style](arkts-arkui-progress-comp-attribute.md#style) attribute settings. For the detailed mapping, see [ProgressStyleMap](arkts-arkui-progress-comp-progressstylemap-i.md).

**Type:** [Type](../arkts-apis/arkts-arkui-arkui-statemanagement-type-d.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressOptions-type?: Type--><!--Device-ProgressOptions-type?: Type-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Specified progress value.

Default value: **0**

Value range: [0, total]. When the value is set less than 0, it is set to 0. When the value is set greater than total, it is set to total. When an invalid value is set, it is handled as the default value.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ProgressOptions-value: number--><!--Device-ProgressOptions-value: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ProgressStyle
```

Specifies the progress bar style.&lt;br

Default value: **ProgressStyle.Linear**

**Type:** [ProgressStyle](arkts-arkui-progress-comp-progressstyle-e.md)

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [type](#type)

<!--Device-ProgressOptions-style?: ProgressStyle--><!--Device-ProgressOptions-style?: ProgressStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
