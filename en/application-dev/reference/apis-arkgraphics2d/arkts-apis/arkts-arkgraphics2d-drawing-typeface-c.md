# Typeface

Describes the style of a typeface, such as SimSun or KaiTi.

> **NOTE:** 
> 
> - This module uses the physical pixel unit, px.
> 
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## getFamilyName

```TypeScript
getFamilyName(): string
```

Obtains the name of the typeface family, which is the name given to a collection of related typeface designs.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| string | Family name. |

## isBold

```TypeScript
isBold(): boolean
```

Checks whether the font is bold.

**Since:** 23

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** if the font is bold; **false** otherwise. |

## isItalic

```TypeScript
isItalic(): boolean
```

Checks whether the font is italic.

**Since:** 23

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** if the font is italic; **false** otherwise. |

## makeFromCurrent

```TypeScript
makeFromCurrent(typefaceArguments: TypefaceArguments): Typeface
```

Constructs a typeface object from the current typeface and its arguments.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | Yes | TypefaceArguments for typeface. |

**Return value:**

| Type | Description |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Typeface object. In abnormal cases, a null pointer is returned. |

## makeFromFile

```TypeScript
static makeFromFile(filePath: string): Typeface
```

Constructs a typeface from a file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Path of the file. For details, see [Mappings Between Application Sandbox Paths and Physical Paths](../../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths). |

**Return value:**

| Type | Description |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Typeface object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## makeFromFileWithArguments

```TypeScript
static makeFromFileWithArguments(filePath: string, typefaceArguments: TypefaceArguments): Typeface
```

Constructs a typeface from the typeface file path and arguments.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Path of the file. For details, see [Mappings Between Application Sandbox Paths and Physical Paths](../../../file-management/app-sandbox-directory.md#mappings-between-application-sandbox-paths-and-physical-paths). |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | Yes | Typeface arguments. |

**Return value:**

| Type | Description |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Typeface object. In abnormal cases, a null pointer is returned. |

## makeFromRawFile

```TypeScript
static makeFromRawFile(rawfile: Resource): Typeface
```

Constructs a typeface from a file, which must be stored in the **resources/rawfile** directory of the application project.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rawfile | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Resource object corresponding to the file. Currently, only resource objects referenced in **&#36;rawfile** format are supported. The corresponding format is **&#36;rawfile('filePath')**, where **filePath** is the relative path of the file to the **resources/rawfile** directory in the project. If the file is stored in **resources/rawfile**, the reference format is **&#36;rawfile('HarmonyOS_Sans_Bold.ttf')**. If the file is stored in a subdirectory, for example, in **resources/rawfile/ttf**, the reference format is **&#36;rawfile('ttf/HarmonyOS_Sans_Bold.ttf')**. |

**Return value:**

| Type | Description |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Typeface object. In abnormal cases, a null pointer is returned. |

## makeFromRawFileWithArguments

```TypeScript
static makeFromRawFileWithArguments(rawfile: Resource, typefaceArguments: TypefaceArguments): Typeface
```

Constructs a typeface from a file with typeface arguments, which must be stored in the **resources/rawfile** directory of the application project.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rawfile | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | Yes | Resource object corresponding to the file. Currently, only resource objects referenced in **&#36;rawfile** format are supported. The corresponding format is **&#36;rawfile('filePath')**, where **filePath** is the relative path of the file to the **resources/rawfile** directory in the project. |
| typefaceArguments | [TypefaceArguments](arkts-arkgraphics2d-drawing-typefacearguments-c.md) | Yes | Typeface arguments. |

**Return value:**

| Type | Description |
| --- | --- |
| [Typeface](arkts-arkgraphics2d-drawing-typeface-c.md) | Typeface object. In abnormal cases, a null pointer is returned. |
