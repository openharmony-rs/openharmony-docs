# Tool

```TypeScript
class Tool
```

A utility class that provides only static methods to convert data structs defined in other modules and [common2D](arkts-arkgraphics2d-graphics-common2d.md).

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 15.
> 
> - This module uses the physical pixel unit, px.
> 
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 15

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## makeColorFromResourceColor

```TypeScript
static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color
```

Converts a color value of the **ResourceColor** type to a **common2D.Color** object.

**Since:** 15

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceColor | ResourceColor | Yes | Color value of the **ResourceColor** type. (All four types of inputs are supported. The following provides 13 example inputs.) The fourth type of [Resource](../../apis-arkui/arkts-apis/arkts-arkui-resource-t.md) supports only the construction method **$r('belonging.type.name')**. Ensure that the resource has been defined in the **main/resources/base/element** directory. (The types **color**, **string**, and **integer** are available for the belonging **app**, whereas only the type **color** is available for the belonging **sys**.) |

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | **Common2D.Color** object. If the conversion fails, a null pointer is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { drawing, common2D } from '@kit.ArkGraphics2D';

// Color
let color1: common2D.Color = drawing.Tool.makeColorFromResourceColor(Color.Blue);

// Number
let color2: common2D.Color = drawing.Tool.makeColorFromResourceColor(0xffc0cb);
let color3: common2D.Color = drawing.Tool.makeColorFromResourceColor(0x11ffa500);

// String
let color4: common2D.Color = drawing.Tool.makeColorFromResourceColor('#ff0000');
let color5: common2D.Color = drawing.Tool.makeColorFromResourceColor('#110000ff');
let color6: common2D.Color = drawing.Tool.makeColorFromResourceColor('#00f');
let color7: common2D.Color = drawing.Tool.makeColorFromResourceColor('#100f');
let color8: common2D.Color = drawing.Tool.makeColorFromResourceColor('rgb(255, 100, 255)');
let color9: common2D.Color = drawing.Tool.makeColorFromResourceColor('rgba(255, 100, 255, 0.5)');

// Resource
let color10: common2D.Color = drawing.Tool.makeColorFromResourceColor($r('sys.color.ohos_id_color_secondary'));

// Use color
let brush = new drawing.Brush();
brush.setColor(color1);
```
