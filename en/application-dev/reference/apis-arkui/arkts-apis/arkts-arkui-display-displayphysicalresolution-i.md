# DisplayPhysicalResolution

Describes the display mode of a device and the corresponding physical screen resolution information.

**Since:** 12

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## foldDisplayMode

```TypeScript
foldDisplayMode: FoldDisplayMode
```

Display mode of the device. The value is **0** for non-foldable devices.

**Type:** [FoldDisplayMode](arkts-arkui-display-folddisplaymode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## physicalHeight

```TypeScript
physicalHeight: number
```

Height of the device, in px. The value is an integer greater than 0.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## physicalWidth

```TypeScript
physicalWidth: number
```

Width of the device, in px. The value is an integer greater than 0.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core
