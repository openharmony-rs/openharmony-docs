# TouchEventData (System API)

Defines the touch event data.

**Since:** 11

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## touchEvent

```TypeScript
touchEvent: TouchEvent
```

Touch event.

**Type:** [TouchEvent](arkts-input-multimodalinput-touchevent-touchevent-i.md)

**Since:** 11

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## useGlobalCoordinate

```TypeScript
useGlobalCoordinate?: boolean
```

Whether to use global coordinates to calculate the injected touch event. The default value is **false**. If this parameter is set to **false**, the coordinates of the relative coordinate system with the upper left corner of the specified screen as the origin are used to calculate the injected touch event. If this parameter is set to **true**, the coordinates of the global coordinate system with the upper left corner of the primary screen as the origin are used to calculate the injected touch event.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.
