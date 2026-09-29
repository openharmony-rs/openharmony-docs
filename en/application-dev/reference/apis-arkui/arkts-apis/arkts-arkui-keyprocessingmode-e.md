# KeyProcessingMode

```TypeScript
declare enum KeyProcessingMode
```

Enumerates the modes for processing key events.

**Since:** 15

<!--Device-unnamed-declare enum KeyProcessingMode--><!--Device-unnamed-declare enum KeyProcessingMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOCUS_NAVIGATION

```TypeScript
FOCUS_NAVIGATION = 0
```

Default value. When the current component does not consume the key event, focus navigation using the **Tab** and arrow keys preferentially stays within the current container.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-KeyProcessingMode-FOCUS_NAVIGATION = 0--><!--Device-KeyProcessingMode-FOCUS_NAVIGATION = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ANCESTOR_EVENT

```TypeScript
ANCESTOR_EVENT = 1
```

When the current component does not consume the key event, focus navigation using the **Tab** and arrow keys is bubbled up to the parent component.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-KeyProcessingMode-ANCESTOR_EVENT = 1--><!--Device-KeyProcessingMode-ANCESTOR_EVENT = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
