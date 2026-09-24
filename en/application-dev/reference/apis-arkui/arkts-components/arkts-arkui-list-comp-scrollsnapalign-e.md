# ScrollSnapAlign

```TypeScript
declare enum ScrollSnapAlign
```

Enumerates the alignment modes of list items when scrolling ends.

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

No alignment. This is the default value.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## START

```TypeScript
START = 1
```

The first item in the view is aligned at the start of the list.

**NOTE:** 

When the list hits the end, the items at the end must be completely displayed. In this case, the items at the start may not be aligned.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CENTER

```TypeScript
CENTER = 2
```

The middle items in the view are aligned in the center of the list.

**NOTE:** 

The top and end items can be aligned to the center of the list. In this case, which may cause empty space to be visible in the list display.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## END

```TypeScript
END = 3
```

The last item in the view is aligned at the end of the list.

**NOTE:** 

When the list hits the start, the items at the start must be completely displayed. In this case, the items at the end may not be aligned.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
