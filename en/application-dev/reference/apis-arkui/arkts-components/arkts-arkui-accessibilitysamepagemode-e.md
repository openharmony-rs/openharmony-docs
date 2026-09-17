# AccessibilitySamePageMode

Enumerates the same-page modes for cross-process embedded components and their host applications. @enum { number }

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SEMI_SILENT

```TypeScript
SEMI_SILENT = 0
```

Ignores initial page loading events and root node page events from the cross-process embedded component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FULL_SILENT

```TypeScript
FULL_SILENT = 1
```

Ignores all page events from the cross-process embedded component.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
