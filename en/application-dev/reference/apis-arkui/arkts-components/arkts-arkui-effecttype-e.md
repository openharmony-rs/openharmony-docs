# EffectType

Enum of using the effects template mode.

**Effect Template: **

| Device Type | Fuzzy Radius (Unit: px) | Saturation | Brightness | Color |  
| -------- | ---- | ---------------------- | -------- | -------- |  
| Mobile device | 0 | 0 | 0 | '#ffffffff', displayed as white.|
| 2-in-1 device: dark mode | 80 | 1.5 | 1.0 | '#e52e3033', displayed as a semi-transparent light red.|
| 2-in-1 device: light mode | 80 | 1.9 | 1.0 | '#e5ffffff', displayed as a semi-transparent dark red.|
| Tablet | 0 | 0 | 0 | '#ffffffff', displayed as white.|

**Since:** 14

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

Define use the effects template defined by the parent effectComponent.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## WINDOW_EFFECT

```TypeScript
WINDOW_EFFECT = 1
```

Define use the effects template defined by the window.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
