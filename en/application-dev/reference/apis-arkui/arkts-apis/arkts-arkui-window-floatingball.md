# @ohos.window.floatingBall

This module provides essential functionalities for floating balls. It lets you check whether the device supports floating balls and create a controller to start, update, or stop them. It is ideal for tasks like comparing prices, searching for answers, or grabbing orders. The floating ball appears as a floating widget above other application, quickly showing important information.

> **NOTE:** 
> 
> - For the system capability SystemCapability.Window.SessionManager, use canIUse() to check whether the device supports this system capability and the corresponding APIs.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatingBall } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [create](arkts-arkui-floatingball-create-f.md) | Creates a floating ball controller. This API uses a promise to return the result. |
| [isFloatingBallEnabled](arkts-arkui-floatingball-isfloatingballenabled-f.md) | Checks whether the device supports floating balls. |

### Interfaces

| Name | Description |
| --- | --- |
| [FloatingBallConfiguration](arkts-arkui-floatingball-floatingballconfiguration-i.md) | Describes the parameters for creating a floating ball controller. |
| [FloatingBallController](arkts-arkui-floatingball-floatingballcontroller-i.md) | Implements a floating ball controller instance, which is used to start, update, and stop floating balls, and register callbacks. |
| [FloatingBallParams](arkts-arkui-floatingball-floatingballparams-i.md) | Describes the parameters for starting and updating the floating ball. |
| [FloatingBallWindowInfo](arkts-arkui-floatingball-floatingballwindowinfo-i.md) | Describes the floating ball window information. |

### Enums

| Name | Description |
| --- | --- |
| [FloatingBallState](arkts-arkui-floatingball-floatingballstate-e.md) | Enumerates the lifecycle states of the floating ball. |
| [FloatingBallTemplate](arkts-arkui-floatingball-floatingballtemplate-e.md) | Enumerates the types of the floating ball template. |
| [FloatingBallTextUpdateAnimationType](arkts-arkui-floatingball-floatingballtextupdateanimationtype-e.md) | Enumerates the animation types used when the floating ball text is updated. |
