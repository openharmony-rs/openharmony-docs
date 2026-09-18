# Tool

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
| resourceColor | ResourceColor | Yes | Color value of the **ResourceColor** type. (All four types of inputs are supported. The following provides 13 example inputs.) The fourth type of [Resource](../../apis-arkui/arkts-apis/arkts-arkui-resource-t.md) supports only the construction method **&#36;r('belonging.type.name')**. Ensure that the resource has been defined in the **main/resources/base/element** directory. (The types **color**, **string**, and **integer** are available for the belonging **app**, whereas only the type **color** is available for the belonging **sys**.) |

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | **Common2D.Color** object. If the conversion fails, a null pointer is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
