# SnapshotSizeLimitation

Defines the size limit of a component screenshot.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## maxHeight

```TypeScript
maxHeight: number
```

Maximum height of a component screenshot.

The normal value range is (0, +∞). A value of -1 indicates that the component snapshot size limitation query failed.

Unit: px.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth: number
```

Maximum width of a component screenshot.

The normal value range is (0, +∞). A value of -1 indicates that the component snapshot size limitation query failed.

Unit: px.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
