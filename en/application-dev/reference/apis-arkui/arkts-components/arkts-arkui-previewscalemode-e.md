# PreviewScaleMode

Enumerates the scale modes of the preview image.

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## AUTO

```TypeScript
AUTO = 0
```

The preview image automatically adjusts its width, height, and scale based on [Placement](../arkts-apis/arkts-arkui-placement-e.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONSTANT

```TypeScript
CONSTANT = 1
```

The preview image retains its original size. However, the preview image may still be compressed or cropped due to the safe area constraints.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MAINTAIN

```TypeScript
MAINTAIN = 2
```

The preview image maintains its aspect ratio when scaled.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
