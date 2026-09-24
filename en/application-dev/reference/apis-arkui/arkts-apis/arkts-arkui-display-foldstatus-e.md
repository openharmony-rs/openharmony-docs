# FoldStatus

```TypeScript
enum FoldStatus
```

Enumerates the fold statuses of a foldable device. For dual-fold axis devices, when oriented with the charging port at the bottom, the hinges are identified from right to left as the first and second fold axes, respectively.

> **NOTE:** 

> Devices with only one fold axis can be in the **FOLD_STATUS_EXPANDED**, **FOLD_STATUS_FOLDED**, or
> **FOLD_STATUS_HALF_FOLDED** state.

> Devices with two fold axes can be in any of the states provided in the table above, except for
> **FOLD_STATUS_UNKNOWN**, which indicates an unusable fold status.

**Since:** 10

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_UNKNOWN

```TypeScript
FOLD_STATUS_UNKNOWN = 0
```

The fold status of the device is unknown or the device cannot be folded.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_EXPANDED

```TypeScript
FOLD_STATUS_EXPANDED = 1
```

The device is fully open. For dual-fold axis devices, the first fold axis is fully open, and the second fold axis is folded.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_FOLDED

```TypeScript
FOLD_STATUS_FOLDED = 2
```

The device is folded (completely closed). For dual-fold axis devices, both the first and second fold axes are folded.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_HALF_FOLDED

```TypeScript
FOLD_STATUS_HALF_FOLDED = 3
```

The device is half-folded, somehow between fully open and completely closed. For dual-fold axis devices, the first fold axis is half-folded, and the second fold axis is folded.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_EXPANDED_WITH_SECOND_EXPANDED

```TypeScript
FOLD_STATUS_EXPANDED_WITH_SECOND_EXPANDED = 11
```

For dual-fold axis devices, both the first and second fold axes are fully open.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_EXPANDED_WITH_SECOND_HALF_FOLDED

```TypeScript
FOLD_STATUS_EXPANDED_WITH_SECOND_HALF_FOLDED = 21
```

For dual-fold axis devices, the first fold axis is fully open, and the second fold axis is half-folded.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_FOLDED_WITH_SECOND_HALF_FOLDED

```TypeScript
FOLD_STATUS_FOLDED_WITH_SECOND_HALF_FOLDED = 22
```

For dual-fold axis devices, the first fold axis is folded, and the second fold axis is fully folded.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_HALF_FOLDED_WITH_SECOND_HALF_FOLDED

```TypeScript
FOLD_STATUS_HALF_FOLDED_WITH_SECOND_HALF_FOLDED = 23
```

For dual-fold axis devices, both the first and second fold axes are half-folded.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_FOLDED_WITH_SECOND_EXPANDED

```TypeScript
FOLD_STATUS_FOLDED_WITH_SECOND_EXPANDED = 12
```

For dual-fold axis devices, the first fold axis is folded, and the second fold axis is fully open.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_STATUS_HALF_FOLDED_WITH_SECOND_EXPANDED

```TypeScript
FOLD_STATUS_HALF_FOLDED_WITH_SECOND_EXPANDED = 13
```

For dual-fold axis devices, the first fold axis is half-folded, and the second fold axis is fully open.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Window.SessionManager
