# Class (Tool)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8cb1e961ff2b923659fd70bcd0083c6e2446d4ab translatedAt=2026-08-24T08:17:55.378Z pushedAt=2026-08-31T03:04:30.361Z -->

The tool class defined in this module provides only static methods and mainly implements the conversion of data structures defined in other modules and [common2D](js-apis-graphics-common2D.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 15.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## makeColorFromResourceColor<sup>15+</sup>

static makeColorFromResourceColor(resourceColor: ResourceColor): common2D.Color

Converts a color value of the **ResourceColor** type to a **common2D.Color** object.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                                              | Mandatory| Description          |
| ------ | -------------------------------------------------- | ---- | -------------- |
| resourceColor | [ResourceColor](../apis-arkui/arkui-ts/ts-types.md#resourcecolor) | Required | Color value in ResourceColor format (all four input types are supported, and 10 sample inputs are provided in the example). The fourth type [Resource](../apis-arkui/arkui-ts/ts-types.md#resource) accepts only the ``$r('belonging.type.name')`` constructor. Ensure that the resource is defined in the main/resources/base/element directory (app supports color, string, and integer, while sys supports only color). |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| [common2D.Color](js-apis-graphics-common2D.md#color) | The converted common2D.Color object, or undefined if the conversion fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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