# BottomOffset

```TypeScript
export declare enum BottomOffset
```

Defines the distance between the popup and the bottom in different scenario modes, based on the presence or absence of a menu bar, with the default being the distance when there is no menu bar.

| Name| Value| Description|  
| - | - | - |  
| [OFFSET_FOR_BAR](arkts-arkui-atomicservice-interstitialdialogaction-bottomoffset-e.md) | 0 | Distance from the bottom of the window when there is a menu bar.It sets the dialog box 88 vp away from the bottom of the window.|

| OFFSET_FOR_NONE | 1 | Distance from the bottom of the window when there is no menu bar.Default value. It sets the dialog box 44 vp away from the bottom of the window.|

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OFFSET_FOR_BAR

```TypeScript
OFFSET_FOR_BAR = 0
```

dialog distance relative to the bottom in the presence of tabs.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OFFSET_FOR_NONE

```TypeScript
OFFSET_FOR_NONE = 1
```

dialog is the distance relative to the bottom without tabs.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
