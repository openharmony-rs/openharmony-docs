# LcdFlashStatus (System API)

```TypeScript
interface LcdFlashStatus
```

Describes the LCD flash information.

**Since:** 12

<!--Device-camera-interface LcdFlashStatus--><!--Device-camera-interface LcdFlashStatus-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isLcdFlashNeeded

```TypeScript
readonly isLcdFlashNeeded: boolean
```

Whether the LCD flash is required. **true** if required, **false** otherwise.

**Type:** boolean

**Since:** 12

<!--Device-LcdFlashStatus-readonly isLcdFlashNeeded: boolean--><!--Device-LcdFlashStatus-readonly isLcdFlashNeeded: boolean-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.

## lcdCompensation

```TypeScript
readonly lcdCompensation: number
```

LCD flash compensation.

**Type:** number

**Since:** 12

<!--Device-LcdFlashStatus-readonly lcdCompensation: int--><!--Device-LcdFlashStatus-readonly lcdCompensation: int-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

**System API:** This is a system API.
