# SwipeInward（系统接口）

向内滑动事件。

**起始版本：** 12

<!--Device-unnamed-export declare interface SwipeInward--><!--Device-unnamed-export declare interface SwipeInward-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { SwipeInward, FourFingersSwipe, Pinch, ActionType, Rotate, ThreeFingersTap, ThreeFingersSwipe, TouchGestureEvent } from '@kit.InputKit';
```

## type

```TypeScript
type: ActionType
```

表示向内滑动事件的类型，固定为SwipeInward。

**类型：** ActionType

**起始版本：** 12

<!--Device-SwipeInward-type: ActionType--><!--Device-SwipeInward-type: ActionType-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## x

```TypeScript
x: number
```

滑动事件触发点的横坐标，单位为像素。

**类型：** number

**起始版本：** 12

<!--Device-SwipeInward-x: int--><!--Device-SwipeInward-x: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

## y

```TypeScript
y: number
```

滑动事件触发点的纵坐标，单位为像素。

**类型：** number

**起始版本：** 12

<!--Device-SwipeInward-y: int--><!--Device-SwipeInward-y: int-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Core

**系统接口：** 此接口为系统接口。

