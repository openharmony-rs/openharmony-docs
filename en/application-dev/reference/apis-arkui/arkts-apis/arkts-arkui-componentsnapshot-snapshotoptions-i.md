# SnapshotOptions

```TypeScript
interface SnapshotOptions
```

Defines the extra options for snapshot taking.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { componentSnapshot } from '@kit.ArkUI';
```

## colorMode

```TypeScript
colorMode?: ColorModeOptions
```

Color space used for the snapshot.

Default value: **{colorSpace: SRGB, isAuto: false}**

**Type:** [ColorModeOptions](arkts-arkui-componentsnapshot-colormodeoptions-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dynamicRangeMode

```TypeScript
dynamicRangeMode?: DynamicRangeModeOptions
```

Dynamic range mode used for the snapshot.

Default value: **{dynamicRangeMode: STANDARD, isAuto: false}**

**Type:** [DynamicRangeModeOptions](arkts-arkui-componentsnapshot-dynamicrangemodeoptions-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## region

```TypeScript
region?: SnapshotRegionType
```

Rectangular region for the snapshot. The default region is the entire component.

**Type:** [SnapshotRegionType](arkts-arkui-componentsnapshot-snapshotregiontype-t.md)

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale?: number
```

Scale ratio for rendering pixel maps during a snapshot. Note that a high scale ratio may increase the time taken for the snapshot or even result in a snapshot failure.

Value range: [0, +∞). If the value is less than or equal to 0, the default value is used.

Default value: **1**

**NOTE:** 

Avoid capturing images that are excessively large, ideally not larger than the screen size. If the size of the image to capture exceeds device-specific underlying limits, the capture will fail.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## waitUntilRenderFinished

```TypeScript
waitUntilRenderFinished?: boolean
```

Whether to force the system to wait for all rendering commands to complete before taking the snapshot. The value **true** means to force the system to wait for all rendering commands to complete before taking the snapshot, and **false** means the opposite. This option ensures the snapshot reflects the most up-to-date content and should be enabled whenever possible. Note that enabling this option may increase the time required for the snapshot to complete, which depends on the size of the area that needs to be redrawn at the time.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
