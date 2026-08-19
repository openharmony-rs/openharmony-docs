# Rotate

旋转手势事件。

**起始版本：** 23

<!--Device-unnamed-export declare interface Rotate--><!--Device-unnamed-export declare interface Rotate-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { ActionType, FourFingersSwipe, Pinch, Rotate, ThreeFingersSwipe, ThreeFingersTap, SwipeInward, TouchGestureEvent } from '@kit.InputKit';
```

## angle

```TypeScript
angle: double
```

旋转角度，单位为度。

**类型：** double

**起始版本：** 23

<!--Device-Rotate-angle: double--><!--Device-Rotate-angle: double-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## type

```TypeScript
type: ActionType
```

手势事件类型。如：手势开始、手势更新、手势结束等。

**类型：** [ActionType](arkts-input-multimodalinput-gestureevent-actiontype-e.md)

**起始版本：** 23

<!--Device-Rotate-type: ActionType--><!--Device-Rotate-type: ActionType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

