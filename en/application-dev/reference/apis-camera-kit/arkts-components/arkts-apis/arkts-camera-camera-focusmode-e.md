# FocusMode

Enumerates the focus modes.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_MANUAL

```TypeScript
FOCUS_MODE_MANUAL = 0
```

Manual focus. The focal length of the camera can be manually set to change the focus position. However, the focal point cannot be set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_CONTINUOUS_AUTO

```TypeScript
FOCUS_MODE_CONTINUOUS_AUTO = 1
```

Continuous auto focus. The focal point cannot be set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_AUTO

```TypeScript
FOCUS_MODE_AUTO = 2
```

Auto focus. The focal point can be set by calling [Focus.setFocusPoint](arkts-camera-camera-focus-i.md#setfocuspoint), and auto focus is performed once based on the focal point.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core

## FOCUS_MODE_LOCKED

```TypeScript
FOCUS_MODE_LOCKED = 3
```

Focus locked. The focal point cannot be set.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Multimedia.Camera.Core
