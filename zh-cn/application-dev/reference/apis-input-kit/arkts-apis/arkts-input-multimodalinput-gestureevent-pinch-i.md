# Pinch

捏合手势事件。

**起始版本：** 23

<!--Device-unnamed-export declare interface Pinch--><!--Device-unnamed-export declare interface Pinch-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { ActionType, FourFingersSwipe, Pinch, Rotate, ThreeFingersSwipe, ThreeFingersTap, SwipeInward, TouchGestureEvent } from '@kit.InputKit';
```

## scale

```TypeScript
scale: double
```

捏合度，取值范围大于等于0。

**类型：** double

**起始版本：** 23

<!--Device-Pinch-scale: double--><!--Device-Pinch-scale: double-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## type

```TypeScript
type: ActionType
```

手势事件类型，包括手势取消、手势开始、手势更新、手势结束。

**类型：** [ActionType](arkts-input-multimodalinput-gestureevent-actiontype-e.md)

**起始版本：** 23

<!--Device-Pinch-type: ActionType--><!--Device-Pinch-type: ActionType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

