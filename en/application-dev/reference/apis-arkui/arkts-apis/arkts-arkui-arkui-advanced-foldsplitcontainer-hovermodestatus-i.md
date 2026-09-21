# HoverModeStatus

```TypeScript
export interface HoverModeStatus
```

Provides device or application information covering fold status, hover mode, application rotation, and window status type.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## appRotation

```TypeScript
appRotation: number
```

App rotation angle, in degrees.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## foldStatus

```TypeScript
foldStatus: display.FoldStatus
```

Fold status of the device, including expanded, half-folded, and fully folded states.

**Type:** [display.FoldStatus](arkts-arkui-display-foldstatus-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isHoverMode

```TypeScript
isHoverMode: boolean
```

Whether the app is currently in hover state. The value **true** indicates hover state, and **false** indicates non-hover state.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowStatusType

```TypeScript
windowStatusType: window.WindowStatusType
```

Window mode, including full-screen, split-screen, and freeform window modes.

**Type:** [window.WindowStatusType](arkts-arkui-window-windowstatustype-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
