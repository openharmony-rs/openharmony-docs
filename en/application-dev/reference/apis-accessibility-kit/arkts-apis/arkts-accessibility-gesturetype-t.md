# GestureType

```TypeScript
type GestureType = 'left' | 'leftThenRight' | 'leftThenUp' | 'leftThenDown''right' | 'rightThenLeft' | 'rightThenUp' | 'rightThenDown''up' | 'upThenLeft' | 'upThenRight' | 'upThenDown''down' | 'downThenLeft' | 'downThenRight' | 'downThenUp''twoFingerSingleTap' | 'twoFingerDoubleTap' | 'twoFingerDoubleTapAndHold' | 'twoFingerTripleTap''twoFingerTripleTapAndHold' | 'threeFingerSingleTap' | 'threeFingerDoubleTap' | 'threeFingerDoubleTapAndHold''threeFingerTripleTap' | 'threeFingerTripleTapAndHold' | 'fourFingerSingleTap' | 'fourFingerDoubleTap''fourFingerDoubleTapAndHold' | 'fourFingerTripleTap' | 'fourFingerTripleTapAndHold''threeFingerSwipeUp' | 'threeFingerSwipeDown' | 'threeFingerSwipeLeft' | 'threeFingerSwipeRight''fourFingerSwipeUp' | 'fourFingerSwipeDown' | 'fourFingerSwipeLeft' | 'fourFingerSwipeRight' | 'oneFingerDoubleTap'
```

Enumerates the gesture event types. A gesture event is triggered by the accessibility service when the user performs a specific gesture operation. The accessibility extension can receive and process the corresponding gesture event through the **onAccessibilityEvent** callback.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type GestureType = 'left' | 'leftThenRight' | 'leftThenUp' | 'leftThenDown' |  'right' | 'rightThenLeft' | 'rightThenUp' | 'rightThenDown' |  'up' | 'upThenLeft' | 'upThenRight' | 'upThenDown' |  'down' | 'downThenLeft' | 'downThenRight' | 'downThenUp' |  'twoFingerSingleTap' | 'twoFingerDoubleTap' | 'twoFingerDoubleTapAndHold' | 'twoFingerTripleTap' |  'twoFingerTripleTapAndHold' | 'threeFingerSingleTap' | 'threeFingerDoubleTap' | 'threeFingerDoubleTapAndHold' |  'threeFingerTripleTap' | 'threeFingerTripleTapAndHold' | 'fourFingerSingleTap' | 'fourFingerDoubleTap' |  'fourFingerDoubleTapAndHold' | 'fourFingerTripleTap' | 'fourFingerTripleTapAndHold' |  'threeFingerSwipeUp' | 'threeFingerSwipeDown' | 'threeFingerSwipeLeft' | 'threeFingerSwipeRight' |  'fourFingerSwipeUp' | 'fourFingerSwipeDown' | 'fourFingerSwipeLeft' | 'fourFingerSwipeRight' | 'oneFingerDoubleTap'--><!--Device-unnamed-type GestureType = 'left' | 'leftThenRight' | 'leftThenUp' | 'leftThenDown' |  'right' | 'rightThenLeft' | 'rightThenUp' | 'rightThenDown' |  'up' | 'upThenLeft' | 'upThenRight' | 'upThenDown' |  'down' | 'downThenLeft' | 'downThenRight' | 'downThenUp' |  'twoFingerSingleTap' | 'twoFingerDoubleTap' | 'twoFingerDoubleTapAndHold' | 'twoFingerTripleTap' |  'twoFingerTripleTapAndHold' | 'threeFingerSingleTap' | 'threeFingerDoubleTap' | 'threeFingerDoubleTapAndHold' |  'threeFingerTripleTap' | 'threeFingerTripleTapAndHold' | 'fourFingerSingleTap' | 'fourFingerDoubleTap' |  'fourFingerDoubleTapAndHold' | 'fourFingerTripleTap' | 'fourFingerTripleTapAndHold' |  'threeFingerSwipeUp' | 'threeFingerSwipeDown' | 'threeFingerSwipeLeft' | 'threeFingerSwipeRight' |  'fourFingerSwipeUp' | 'fourFingerSwipeDown' | 'fourFingerSwipeLeft' | 'fourFingerSwipeRight' | 'oneFingerDoubleTap'-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'left' | Left gesture. |
| 'leftThenRight' | Left-then-right gesture. |
| 'leftThenUp' | Left-then-up gesture. |
| 'leftThenDown' | Left-then-down gesture. |
| 'right' | Right gesture. |
| 'rightThenLeft' | Right-then-left gesture. |
| 'rightThenUp' | Right-then-up gesture. |
| 'rightThenDown' | Right-then-down gesture. |
| 'up' | Up gesture. |
| 'upThenLeft' | Up-then-left gesture. |
| 'upThenRight' | Up-then-right gesture. |
| 'upThenDown' | Up-then-down gesture. |
| 'down' | Down gesture. |
| 'downThenLeft' | Down-then-left gesture. |
| 'downThenRight' | Down-then-right gesture. |
| 'downThenUp' | Down-then-up gesture. |
| 'twoFingerSingleTap' | Two-finger single-tap gesture.<br>**Since:** 11 |
| 'twoFingerDoubleTap' | Two-finger double-tap gesture.<br>**Since:** 11 |
| 'twoFingerDoubleTapAndHold' | Two-finger double-tap-and-hold gesture.<br>**Since:** 11 |
| 'twoFingerTripleTap' | Two-finger triple-tap gesture.<br>**Since:** 11 |
| 'twoFingerTripleTapAndHold' | Two-finger triple-tap-and-hold gesture.<br>**Since:** 11 |
| 'threeFingerSingleTap' | Three-finger single-tap gesture.<br>**Since:** 11 |
| 'threeFingerDoubleTap' | Three-finger double-tap gesture.<br>**Since:** 11 |
| 'threeFingerDoubleTapAndHold' | Three-finger double-tap-and-hold gesture.<br>**Since:** 11 |
| 'threeFingerTripleTap' | Three-finger triple-tap gesture.<br>**Since:** 11 |
| 'threeFingerTripleTapAndHold' | Three-finger triple-tap-and-hold gesture.<br>**Since:** 11 |
| 'fourFingerSingleTap' | Four-finger single-tap gesture.<br>**Since:** 11 |
| 'fourFingerDoubleTap' | Four-finger double-tap gesture.<br>**Since:** 11 |
| 'fourFingerDoubleTapAndHold' | Four-finger double-tap-and-hold gesture.<br>**Since:** 11 |
| 'fourFingerTripleTap' | Four-finger triple-tap gesture.<br>**Since:** 11 |
| 'fourFingerTripleTapAndHold' | Four-finger triple-tap-and-hold gesture.<br>**Since:** 11 |
| 'threeFingerSwipeUp' | Three-finger swipe-up gesture.<br>**Since:** 11 |
| 'threeFingerSwipeDown' | Three-finger swipe-down gesture.<br>**Since:** 11 |
| 'threeFingerSwipeLeft' | Three-finger swipe-left gesture.<br>**Since:** 11 |
| 'threeFingerSwipeRight' | Three-finger swipe-right gesture.<br>**Since:** 11 |
| 'fourFingerSwipeUp' | Four-finger swipe-up gesture.<br>**Since:** 11 |
| 'fourFingerSwipeDown' | Four-finger swipe-down gesture.<br>**Since:** 11 |
| 'fourFingerSwipeLeft' | Four-finger swipe-left gesture.<br>**Since:** 11 |
| 'fourFingerSwipeRight' | Four-finger swipe-right gesture.<br>**Since:** 11 |
| 'oneFingerDoubleTap' | Single-finger double-tap gesture.<br>**Since:** 26.0.0 |
