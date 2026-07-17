# Pinch

捏合手势事件。

**起始版本：** 10

<!--Device-unnamed-export declare interface Pinch--><!--Device-unnamed-export declare interface Pinch-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## 导入模块

```TypeScript
import { SwipeInward, FourFingersSwipe, Pinch, ActionType, Rotate, ThreeFingersTap, ThreeFingersSwipe, TouchGestureEvent } from '@kit.InputKit';
```

## scale

```TypeScript
scale: number
```

捏合度，取值范围大于等于0。

**类型：** number

**起始版本：** 10

<!--Device-Pinch-scale: double--><!--Device-Pinch-scale: double-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

## type

```TypeScript
type: ActionType
```

手势事件类型。如：手势开始、手势更新、手势结束等。

**类型：** ActionType

**起始版本：** 10

<!--Device-Pinch-type: ActionType--><!--Device-Pinch-type: ActionType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

