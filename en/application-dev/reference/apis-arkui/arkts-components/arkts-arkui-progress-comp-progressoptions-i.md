# ProgressOptions

```TypeScript
declare interface ProgressOptions<Type extends keyof ProgressStyleMap>
```

Defines progress bar options.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ProgressStyle
```

Style of the progress indicator.

This parameter is deprecated since API version 8. You are advised to use **type** instead.

Default value: **ProgressStyle.Linear**

**Type:** [ProgressStyle](arkts-arkui-progress-comp-progressstyle-e.md)

**Since:** 7

**Deprecated since:** 8

**Substitutes:** [type](#type)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## total

```TypeScript
total?: number
```

Total progress. If this parameter is set to a value less than or equal to 0, the value **100** is used.

Default value: **100**

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: Type
```

Style of the progress indicator.

Default value: **ProgressType.Linear**

**Type:** [Type](../arkts-apis/arkts-arkui-arkui-statemanagement-type-d.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Current progress. Values less than 0 are adjusted to **0**, and values greater than the **total** value are capped at the **total** value.

Default value: **0**

Value range: [0, total]

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
