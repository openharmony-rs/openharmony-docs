# Class (TypefaceArguments)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=420af6019e8cfddc483defe1fc789f2af88ace4e translatedAt=2026-08-24T08:19:02.269Z pushedAt=2026-08-31T03:08:13.673Z -->

Provides a class for configuring font attributes, used to configure the attribute parameters of a variable font (such as axis tags like the font weight dimension and their corresponding attribute values).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 20.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor<sup>20+</sup>

constructor()

Constructor for typeface arguments.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
let typefaceArgument = new drawing.TypefaceArguments();
```

## addVariation<sup>20+</sup>

addVariation(axis: string, value: number)

Adds a variable dimension axis tag and its corresponding attribute value to the font attributes.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description            |
| ----------- | ---------------------------------------- | ---- | -------------------   |
| axis  | string           | Yes   | Variable dimension axis tag of the font attribute object. The supported tags depend on the loaded font file. For details about the supported attributes and tag values, see the corresponding font file.   |
| value | number           | Yes  | Value linked to the **'wght'** tag for the weight variation in the **typeFaceArgument** object. The value must be within the range defined in the typeface file. Otherwise, the value does not take effect. Values below the minimum will be set to the minimum and values above the maximum to the maximum. For details, check the typeface file.   |

**Error codes**

For details about the following error code, see [Drawing and Display Error Codes](../apis-arkgraphics2d/errorcode-drawing.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 25900001 | Parameter error.Possible causes: Incorrect parameter range. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let typefaceArgument = new drawing.TypefaceArguments();
typefaceArgument.addVariation('wght', 10);
```