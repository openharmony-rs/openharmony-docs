# GesturePoint

Represents a gesture touch point, which is the basic unit that constitutes a GesturePath node and is used to define the touch position in the gesture trajectory for accessibility gesture injection. For details about how to use it, see [GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md).

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## Modules to Import

```TypeScript
import { GesturePoint } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(positionX: number, positionY: number)
```

Creates a **GesturePoint** instance based on the given X and Y coordinates.

**Since:** 9

**Deprecated since:** 12

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| positionX | number | Yes | X coordinate of the touch point, in pixels (px). |
| positionY | number | Yes | Y coordinate of the touch point, in pixels (px). |

**Examples**

```TypeScript
import { GesturePoint } from '@kit.AccessibilityKit';

let gesturePoint = new GesturePoint(1, 2);
```

## positionX

```TypeScript
positionX: number
```

X coordinate of the touch point, in pixels (px).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

## positionY

```TypeScript
positionY: number
```

Y coordinate of the touch point, in pixels (px).

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core
