# DatePickerResult

Defines the time format returned by the date picker.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## day

```TypeScript
day?: number
```

Day of the selected date.

Value range: depends on **start** and **end**. If **start** and **end** are not set, the default range is [1, 31].

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## month

```TypeScript
month?: number
```

Zero-based month index of the selected date. **0** indicates January, and **11** indicates December.

Value range: depends on **start** and **end**. If **start** and **end** are not set, the default range is [0, 11].

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## year

```TypeScript
year?: number
```

Year of the selected date.

Value range: depends on **start** and **end**. If **start** and **end** are not set, the default range is [1970, 2100].

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
