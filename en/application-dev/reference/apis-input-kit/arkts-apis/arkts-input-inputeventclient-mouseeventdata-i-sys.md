# MouseEventData (System API)

Defines the mouse event data.

**Since:** 11

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## mouseEvent

```TypeScript
mouseEvent: MouseEvent
```

Mouse event.

**Type:** [MouseEvent](arkts-input-multimodalinput-mouseevent-mouseevent-i.md)

**Since:** 11

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.

## useGlobalCoordinate

```TypeScript
useGlobalCoordinate? : boolean
```

Whether to use global coordinates to calculate the injected mouse event. The default value is **false**. If this parameter is set to **false**, the coordinates of the relative coordinate system with the upper left corner of the specified screen as the origin are used to calculate the injected mouse event. If this parameter is set to **true**, the coordinates of the global coordinate system with the upper left corner of the primary screen as the origin are used to calculate the injected mouse event.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

**System API:** This is a system API.
