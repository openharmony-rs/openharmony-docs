# TextDisplayState

Enumerates text display states. Native result after text typesetting, which is irrelevant to external display factors such as external canvas cropping and screen overflow.

**Since:** 26.0.0

**System capability:** SystemCapability.Graphics.Drawing

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Unknown display state, which is the default state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## ALL

```TypeScript
ALL = 1
```

Complete display state, in which the text is not truncated or omitted and all content is displayed normally.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## CLIP

```TypeScript
CLIP = 2
```

Cropping display state, in which the part of the text that exceeds the typesetting area is directly cropped and hidden.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## OMITTED

```TypeScript
OMITTED = 3
```

Ellipsized display state, in which part of the content is replaced by specified characters (such as ellipsis '...') when the text exceeds the typesetting area.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing
