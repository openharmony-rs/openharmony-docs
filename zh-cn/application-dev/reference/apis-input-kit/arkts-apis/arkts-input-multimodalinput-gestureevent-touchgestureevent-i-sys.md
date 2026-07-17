# TouchGestureEvent（系统接口）

触摸屏手势事件。

**起始版本：** 18

<!--Device-unnamed-export declare interface TouchGestureEvent--><!--Device-unnamed-export declare interface TouchGestureEvent-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { SwipeInward, FourFingersSwipe, Pinch, ActionType, Rotate, ThreeFingersTap, ThreeFingersSwipe, TouchGestureEvent } from '@kit.InputKit';
```

## action

```TypeScript
action: TouchGestureAction
```

触摸屏手势类型。

**类型：** TouchGestureAction

**起始版本：** 18

<!--Device-TouchGestureEvent-action: TouchGestureAction--><!--Device-TouchGestureEvent-action: TouchGestureAction-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## touches

```TypeScript
touches: Touch[]
```

触屏点信息。

**类型：** Touch[]

**起始版本：** 18

<!--Device-TouchGestureEvent-touches: Touch[]--><!--Device-TouchGestureEvent-touches: Touch[]-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

