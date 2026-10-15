# AreaChangeOptions

```TypeScript
declare interface AreaChangeOptions
```

Parameters related to area change.

@typedef AreaChangeOptions

**Since:** 26.0.0

<!--Device-unnamed-declare interface AreaChangeOptions--><!--Device-unnamed-declare interface AreaChangeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## expectedUpdateInterval

```TypeScript
expectedUpdateInterval?: number
```

Expected update interval of the area change, in ms. If this field is greater than 2^31-1, the value is set to 2^31-1. If this field is less than 0 or not set, the default value 1000 is used.

Default value: **1000**

Value range: [0, 2^31-1]

**Type:** number

**Default:** 1000

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-AreaChangeOptions-expectedUpdateInterval?: int--><!--Device-AreaChangeOptions-expectedUpdateInterval?: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
