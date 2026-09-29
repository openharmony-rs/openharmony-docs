# LcdFlashStatus（系统接口）

```TypeScript
interface LcdFlashStatus
```

Describes the LCD flash information.

**起始版本：** 12

<!--Device-camera-interface LcdFlashStatus--><!--Device-camera-interface LcdFlashStatus-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isLcdFlashNeeded

```TypeScript
readonly isLcdFlashNeeded: boolean
```

Whether the LCD flash is required. **true** if required, **false** otherwise.

**类型：** boolean

**起始版本：** 12

<!--Device-LcdFlashStatus-readonly isLcdFlashNeeded: boolean--><!--Device-LcdFlashStatus-readonly isLcdFlashNeeded: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## lcdCompensation

```TypeScript
readonly lcdCompensation: number
```

LCD flash compensation.

**类型：** number

**起始版本：** 12

<!--Device-LcdFlashStatus-readonly lcdCompensation: int--><!--Device-LcdFlashStatus-readonly lcdCompensation: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
