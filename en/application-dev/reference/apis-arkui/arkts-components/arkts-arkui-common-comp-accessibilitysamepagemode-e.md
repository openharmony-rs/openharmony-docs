# AccessibilitySamePageMode

```TypeScript
declare enum AccessibilitySamePageMode
```

Enumerates the same-page modes for cross-process embedded components and their host applications.

**Since:** 18

<!--Device-unnamed-declare enum AccessibilitySamePageMode--><!--Device-unnamed-declare enum AccessibilitySamePageMode-End-->

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

<!--Device-AccessibilitySamePageMode-FULL_SILENT = 1--><!--Device-AccessibilitySamePageMode-FULL_SILENT = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SEMI_SILENT

```TypeScript
SEMI_SILENT = 0
```

The page event sent when the page is loaded for the first time in the process started by a component displayed in cross-process embedding, and the page event sent by the root node of the page, will be ignored.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-AccessibilitySamePageMode-SEMI_SILENT = 0--><!--Device-AccessibilitySamePageMode-SEMI_SILENT = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
