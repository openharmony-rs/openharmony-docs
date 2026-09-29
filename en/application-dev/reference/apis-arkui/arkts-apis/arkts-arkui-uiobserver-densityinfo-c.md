# DensityInfo

```TypeScript
export class DensityInfo
```

Provides the information contained in the callback when the screen pixel density changes.

**Since:** 12

<!--Device-uiObserver-export class DensityInfo--><!--Device-uiObserver-export class DensityInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## context

```TypeScript
context: UIContext
```

Context corresponding to the page when the screen pixel density changes.

**Type:** UIContext

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DensityInfo-context: UIContext--><!--Device-DensityInfo-context: UIContext-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## density

```TypeScript
density: number
```

Screen pixel density after the change.

Value range: [0, +∞)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DensityInfo-density: number--><!--Device-DensityInfo-density: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
