# SnapshotSizeLimitation

```TypeScript
interface SnapshotSizeLimitation
```

Defines the size limit of a component screenshot.

**Since:** 26.0.0

<!--Device-componentSnapshot-interface SnapshotSizeLimitation--><!--Device-componentSnapshot-interface SnapshotSizeLimitation-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## maxHeight

```TypeScript
maxHeight: number
```

Maximum height for the component snapshot.

Value range: [0, +∞).

Unit: px.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SnapshotSizeLimitation-maxHeight: int--><!--Device-SnapshotSizeLimitation-maxHeight: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth: number
```

Maximum width for the component snapshot.

Value range: [0, +∞).

Unit: px.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-SnapshotSizeLimitation-maxWidth: int--><!--Device-SnapshotSizeLimitation-maxWidth: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
