# FingerprintEvent（系统接口）

指纹手势事件的类型和相对侧边指纹器件的偏移位置。

**起始版本：** 23

<!--Device-unnamed-export declare interface FingerprintEvent--><!--Device-unnamed-export declare interface FingerprintEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { shortKey } from '@kit.InputKit';
import { FingerprintEvent } from '@kit.InputKit';
```

## action

```TypeScript
action: FingerprintAction
```

指纹手势事件类型的枚举。

**类型：** [FingerprintAction](arkts-input-multimodalinput-shortkey-fingerprintaction-e-sys.md)

**起始版本：** 23

<!--Device-FingerprintEvent-action: FingerprintAction--><!--Device-FingerprintEvent-action: FingerprintAction-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## distanceX

```TypeScript
distanceX: double
```

相对于侧边指纹器件短轴偏移量（正数表示向右移动，负数表示向左移动）。

**类型：** double

**起始版本：** 23

<!--Device-FingerprintEvent-distanceX: double--><!--Device-FingerprintEvent-distanceX: double-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## distanceY

```TypeScript
distanceY: double
```

相对于侧边指纹器件长轴偏移量（正数表示向上移动，负数表示向下移动）。

**类型：** double

**起始版本：** 23

<!--Device-FingerprintEvent-distanceY: double--><!--Device-FingerprintEvent-distanceY: double-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

