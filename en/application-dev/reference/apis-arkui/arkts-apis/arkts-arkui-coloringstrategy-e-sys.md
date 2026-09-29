# ColoringStrategy

```TypeScript
declare enum ColoringStrategy
```

Enumerates the coloring strategies.

**Since:** 10

<!--Device-unnamed-declare enum ColoringStrategy--><!--Device-unnamed-declare enum ColoringStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CONTRAST

```TypeScript
CONTRAST = 'contrast'
```

Extract the average color from the component background and convert to a contrasting black or white color. Child components can use this color through Color('foreground').

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ColoringStrategy-CONTRAST = 'contrast'--><!--Device-ColoringStrategy-CONTRAST = 'contrast'-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
