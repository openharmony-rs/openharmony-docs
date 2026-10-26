# ShadowClipMode

```TypeScript
declare enum ShadowClipMode
```

Enumerates the clip modes for the shadow when it is not filled.

**Since:** 26.1.0

<!--Device-unnamed-declare enum ShadowClipMode--><!--Device-unnamed-declare enum ShadowClipMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## BOUNDS_SHAPE

```TypeScript
BOUNDS_SHAPE = 1
```

Clip the shadow by the component bounds.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ShadowClipMode-BOUNDS_SHAPE = 1--><!--Device-ShadowClipMode-BOUNDS_SHAPE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT_SHAPE

```TypeScript
DEFAULT_SHAPE = 0
```

Clip the shadow by the default shape (priority order: shadowShape &gt; clipShape &gt; component bounds).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-ShadowClipMode-DEFAULT_SHAPE = 0--><!--Device-ShadowClipMode-DEFAULT_SHAPE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
