# FocusMode

```TypeScript
enum FocusMode
```

Enumerates the focus modes.

**Since:** 10

<!--Device-camera-enum FocusMode--><!--Device-camera-enum FocusMode-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_MANUAL

```TypeScript
FOCUS_MODE_MANUAL = 0
```

Manual focus. The focal length of the camera can be manually set to change the focus position. However, the focal point cannot be set.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FocusMode-FOCUS_MODE_MANUAL = 0--><!--Device-FocusMode-FOCUS_MODE_MANUAL = 0-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_CONTINUOUS_AUTO

```TypeScript
FOCUS_MODE_CONTINUOUS_AUTO = 1
```

Continuous auto focus. The focal point cannot be set.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FocusMode-FOCUS_MODE_CONTINUOUS_AUTO = 1--><!--Device-FocusMode-FOCUS_MODE_CONTINUOUS_AUTO = 1-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_AUTO

```TypeScript
FOCUS_MODE_AUTO = 2
```

Auto focus. The focal point can be set by calling [Focus.setFocusPoint](arkts-camera-camera-focus-i.md#setfocuspoint), and auto focus is performed once based on the focal point.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FocusMode-FOCUS_MODE_AUTO = 2--><!--Device-FocusMode-FOCUS_MODE_AUTO = 2-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_LOCKED

```TypeScript
FOCUS_MODE_LOCKED = 3
```

Focus locked. The focal point cannot be set.

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FocusMode-FOCUS_MODE_LOCKED = 3--><!--Device-FocusMode-FOCUS_MODE_LOCKED = 3-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
