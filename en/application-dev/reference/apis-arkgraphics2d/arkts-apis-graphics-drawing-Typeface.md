# Class (Typeface)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d66ce495242bdf35b08a89dbf23cdf3929953623 translatedAt=2026-08-24T08:20:00.042Z pushedAt=2026-08-31T03:05:25.656Z -->

The Typeface class is used to represent and manage font objects. Supported font operations include obtaining the font family name, constructing a font from a font file or rawfile resource, constructing a new font by combining font attributes, and checking whether a font is bold or italic.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## getFamilyName

getFamilyName(): string

Obtains the name of the typeface family, which is the name given to a collection of related typeface designs.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| string | Font family name, which indicates the font design name corresponding to the current Typeface object. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const font = new drawing.Font();
let typeface = font.getTypeface();
let familyName = typeface.getFamilyName();
```

## makeFromCurrent<sup>20+</sup>

makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface

Constructs a typeface object from the current typeface and its arguments.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| typefaceArguments | [TypefaceArguments](arkts-apis-graphics-drawing-TypefaceArguments.md)           | Yes   | Font attribute parameter. |

**Returns**

| Type  | Description                 |
| ------ | -------------------- |
| [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Returns a font object constructed by combining the current font with font attributes (a null pointer is returned in exception cases). |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class TextRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    const canvas = context.canvas;
    let typeArguments = new drawing.TypefaceArguments();
    typeArguments.addVariation("wght", 100);
    const myTypeFace = drawing.Typeface.makeFromFile("/system/fonts/HarmonyOS_Sans_SC.ttf");
    const typeFace1 = myTypeFace.makeFromCurrent(typeArguments);
    let font = new drawing.Font();
    font.setTypeface(typeFace1);
    const textBlob = drawing.TextBlob.makeFromString("Hello World", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 60, 100);
  }
}
```

## makeFromFile<sup>12+</sup>

static makeFromFile(filePath: string): Typeface

Constructs a typeface from a file.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| filePath | string           | Yes  | Path of the file. For details, see [Mappings Between Application Sandbox Paths and Physical Paths](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths).|

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Returns the font object loaded from the specified font file. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class TextRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    let str = "/system/fonts/HarmonyOS_Sans_Italic.ttf";
    const mytypeface = drawing.Typeface.makeFromFile(str);
    font.setTypeface(mytypeface);
    const textBlob = drawing.TextBlob.makeFromString("Hello World", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 60, 100);
  }
}
```

## makeFromRawFile<sup>18+</sup>

static makeFromRawFile(rawfile: Resource): Typeface

Constructs a font using the specified font file, which must be stored in the rawfile directory of the application resource folder.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| rawfile | [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)           | Yes  | Resource object corresponding to the file. Currently, only resource objects referenced in **$rawfile** format are supported. The corresponding format is **$rawfile('filePath')**, where **filePath** is the relative path of the file to the **resources/rawfile** directory in the project. If the file is stored in **resources/rawfile**, the reference format is **$rawfile('HarmonyOS_Sans_Bold.ttf')**. If the file is stored in a subdirectory, for example, in **resources/rawfile/ttf**, the reference format is **$rawfile('ttf/HarmonyOS_Sans_Bold.ttf')**.|

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Returns the font object loaded from a rawfile resource (a null pointer is returned in exception cases). |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class TextRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    const myTypeFace = drawing.Typeface.makeFromRawFile($rawfile('HarmonyOS_Sans_Bold.ttf'));
    font.setTypeface(myTypeFace);
    const textBlob = drawing.TextBlob.makeFromString("Hello World", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 60, 100);
  }
}

```

## makeFromFileWithArguments<sup>20+</sup>

static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface

Constructs a typeface from the typeface file path and arguments.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| filePath | string           | Yes  | Path of the file. For details, see [Mappings Between Application Sandbox Paths and Physical Paths](../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths).|
| typefaceArguments | [TypefaceArguments](arkts-apis-graphics-drawing-TypefaceArguments.md) | Yes | Font attribute parameter. |

**Returns**

| Type  | Description                 |
| ------ | -------------------- |
| [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Returns the font object loaded from the specified font file and constructed by combining font attributes (a null pointer is returned in exception cases). |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class TextRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    let str = "/system/fonts/HarmonyOS_Sans_Italic.ttf";
    let typeFaceArgument = new drawing.TypefaceArguments();
    const myTypeFace = drawing.Typeface.makeFromFileWithArguments(str, typeFaceArgument);
    font.setTypeface(myTypeFace);
    const textBlob = drawing.TextBlob.makeFromString("Hello World", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 60, 100);
  }
}
```

## makeFromRawFileWithArguments<sup>20+</sup>

static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface

Constructs a new font using the specified font file and font attributes. The font file must be stored in the rawfile directory of the application resource folder.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| rawfile | [Resource](../apis-arkui/arkui-ts/ts-types.md#resource)           | Yes   | Specifies the resource object corresponding to the font file. Currently, only resource objects referenced in the ``$rawfile`` format are supported. A null pointer is returned when a resource object in a non-``$rawfile`` format is passed in. The corresponding format is written as ``$rawfile('filePath')``, where filePath is the relative path of the specified font file to the resources/rawfile directory in the project. |
| typefaceArguments | [TypefaceArguments](arkts-apis-graphics-drawing-TypefaceArguments.md) | Yes | Font attribute parameters. |

**Returns**

| Type  | Description                |
| ------ | ------------------- |
| [Typeface](arkts-apis-graphics-drawing-Typeface.md) | Returns the font object loaded from a rawfile resource and constructed with font attributes (a null pointer is returned in exception cases). |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class TextRenderNode extends RenderNode {
  async draw(context: DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    let typeFaceArgument = new drawing.TypefaceArguments();
    const myTypeFace = drawing.Typeface.makeFromRawFileWithArguments($rawfile('HarmonyOS_Sans_Bold.ttf'), typeFaceArgument);
    font.setTypeface(myTypeFace);
    const textBlob = drawing.TextBlob.makeFromString("Hello World", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    canvas.drawTextBlob(textBlob, 60, 100);
  }
}
```

## isBold<sup>23+</sup>

isBold(): boolean

Checks whether the font is bold.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| boolean | Check result. **true** if the font is bold; **false** otherwise.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const font = new drawing.Font();
let typeface = font.getTypeface();
let result = typeface.isBold();
```

## isItalic<sup>23+</sup>

isItalic(): boolean

Checks whether the font is italic.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type  | Description                |
| ------ | -------------------- |
| boolean | Whether the current font is italic. The value true indicates that the font is italic, and false indicates the opposite. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const font = new drawing.Font();
let typeface = font.getTypeface();
let result = typeface.isItalic();
```