# convertGlobalToRelativeCoordinate

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## convertGlobalToRelativeCoordinate

```TypeScript
function convertGlobalToRelativeCoordinate(position: Position, displayId?: number): RelativePosition
```

Converts global coordinates (based on the top-left corner of the primary screen) into relative coordinates (based on the top-left corner of the screen specified by **displayId**). This API supports only coordinate conversion between the primary screen and extended screen. If **displayId** is not passed, the coordinates are converted relative to the screen where the global coordinates are located. If the global coordinates are not on any screen, the coordinates are converted relative to the primary screen by default.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | [Position](arkts-arkui-display-position-i.md) | Yes | Global coordinates to convert. |
| displayId | number | No | Display ID for the relative coordinates. If this parameter is passed, the coordinates are converted relative to this screen. If it is not provided, the coordinates are converted to the screen where the global coordinates are located, or the primary screen if they are not on any screen. |

**Return value:**

| Type | Description |
| --- | --- |
| [RelativePosition](arkts-arkui-display-relativeposition-i.md) | Relative coordinates for the specified screen. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [1400003](../errorcode-display.md#1400003-abnormal-display-manager-service) | This display manager service works abnormally. |
| [1400004](../errorcode-display.md#1400004-parameter-error) | Parameter error. Possible cause: 1. Invalid parameter range. |

**Examples**

```TypeScript
// Define the global coordinates to convert.
let position: display.Position = {
    x: 100,
    y: 200
};

try {
  // Convert the global coordinates to relative coordinates.
  let relPos: display.RelativePosition = display.convertGlobalToRelativeCoordinate(position, 0);
  console.info(`The relative coordinate is ${relPos.displayId}, ${relPos.position.x}, ${relPos.position.y}`);
} catch (exception) {
  console.error(`Failed to convert the global coordinate to the relative coordinate. Code: ${exception.code}, message: ${exception.message}`);
}
```
