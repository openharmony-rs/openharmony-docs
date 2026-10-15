# SnapshotRegion

```TypeScript
interface SnapshotRegion
```

Defines the rectangular region for capturing the component snapshot.

**Since:** 15

<!--Device-componentSnapshot-interface SnapshotRegion--><!--Device-componentSnapshot-interface SnapshotRegion-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## bottom

```TypeScript
bottom: number
```

Y-coordinate of the lower right corner of the rectangular region.

Unit: px.

Value range: [0, Component height]. If the value is out of range, the snapshot fails and error code 401 is returned.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SnapshotRegion-bottom: number--><!--Device-SnapshotRegion-bottom: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left: number
```

X-coordinate of the upper left corner of the rectangular region.

Unit: px.

Value range: [0, Component width]. If the value is out of range, the snapshot fails and error code 401 is returned.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SnapshotRegion-left: number--><!--Device-SnapshotRegion-left: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right: number
```

X-coordinate of the lower right corner of the rectangular region.

Unit: px.

Value range: [0, Component width]. If the value is out of range, the snapshot fails and error code 401 is returned.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SnapshotRegion-right: number--><!--Device-SnapshotRegion-right: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top: number
```

Y-coordinate of the upper left corner of the rectangular region.

Unit: px.

Value range: [0, Component height]. If the value is out of range, the snapshot fails and error code 401 is returned.

**Type:** number

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-SnapshotRegion-top: number--><!--Device-SnapshotRegion-top: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
