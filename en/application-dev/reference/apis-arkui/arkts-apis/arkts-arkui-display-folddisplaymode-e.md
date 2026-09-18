# FoldDisplayMode

Enumerates the display modes of a foldable device.

> **NOTE:** 

> For foldable devices where both the inner and outer screens can serve as the primary screen �� like large or wide-
> folding models �� the inner screen's display mode is **FOLD_DISPLAY_MODE_FULL**, and the outer screen's display
> mode is **FOLD_DISPLAY_MODE_MAIN**.

> For foldable devices where the outer screen serves only as an auxiliary display �� like small-folding models �� the
> inner screen's display mode is **FOLD_DISPLAY_MODE_MAIN**, and the outer screen's display mode is
> **FOLD_DISPLAY_MODE_SUB**.

**Since:** 10

**System capability:** SystemCapability.Window.SessionManager

## FOLD_DISPLAY_MODE_UNKNOWN

```TypeScript
FOLD_DISPLAY_MODE_UNKNOWN = 0
```

The display mode of the device is unknown.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_DISPLAY_MODE_FULL

```TypeScript
FOLD_DISPLAY_MODE_FULL = 1
```

The device is displayed in full screen.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_DISPLAY_MODE_MAIN

```TypeScript
FOLD_DISPLAY_MODE_MAIN = 2
```

The primary screen of the device is displayed.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_DISPLAY_MODE_SUB

```TypeScript
FOLD_DISPLAY_MODE_SUB = 3
```

The secondary screen of the device is displayed.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## FOLD_DISPLAY_MODE_COORDINATION

```TypeScript
FOLD_DISPLAY_MODE_COORDINATION
```

Both screens of the device are displayed in collaborative mode.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager
