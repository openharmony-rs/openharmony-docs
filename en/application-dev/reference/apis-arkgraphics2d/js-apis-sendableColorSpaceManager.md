# @ohos.graphics.sendableColorSpaceManager (Sendable Color Space Management)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @xiaojianfeng_jeffery-->
<!--Designer: @dizuo1-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

This module provides APIs for creating and managing sendable color space objects and obtaining basic attributes of sendable color spaces. It is applicable to scenarios where color space information needs to be transferred between multiple threads. It solves the problem that color management objects cannot be shared across threads, improving the efficiency and consistency of color processing.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { sendableColorSpaceManager } from '@kit.ArkGraphics2D';
```

## ISendable
type ISendable = lang.ISendable

The ISendable type alias is defined to align with the API specifications of the current module.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

| Type               | Description                    |
| ------------------ | ------------------------ |
| [lang.ISendable](../apis-arkts/js-apis-arkts-lang.md#langisendable)  | Parent type of all sendable types.              |

## sendableColorSpaceManager.create

create(colorSpaceName: colorSpaceManager.ColorSpace): ColorSpaceManager

Creates a criterion color space management instance that is sendable.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Parameters**

| Name          | Type                    | Mandatory| Description                         |
| --------------- | ------------------------ | ---- | -----------------------------|
| colorSpaceName  | [colorSpaceManager.ColorSpace](js-apis-colorSpaceManager.md#colorspace)| Yes  | Type of the color space.<br>**UNKNOWN** and **CUSTOM** cannot be used when creating standard color space objects.      |

**Return value**

| Type               | Description                    |
| ------------------ | ------------------------ |
| [ColorSpaceManager](#colorspacemanager)  | Sendable color space object created.<br>This instance inherits from **ISendable** and can be passed by reference between concurrent ArkTS instances (including the main thread and the worker threads of TaskPool or Worker). For details, see [Using Sendable Objects](../../arkts-utils/sendable-guide.md).                |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [colorSpaceManager Error Codes](errorcode-colorspace-manager.md).

| ID| Error Message|
| ------- | ----------------------- |
| 401 | Parameter error. Possible cause: 1. Incorrect parameter type. 2. Parameter verification failed.|
| 18600001 | The parameter value is abnormal. |

**Example**

```ts
import { colorSpaceManager, sendableColorSpaceManager } from '@kit.ArkGraphics2D';
let colorSpace: sendableColorSpaceManager.ColorSpaceManager;
// Create a color management instance for the criterion sRGB color space.
colorSpace = sendableColorSpaceManager.create(colorSpaceManager.ColorSpace.SRGB);
```

## sendableColorSpaceManager.create

create(primaries: colorSpaceManager.ColorSpacePrimaries, gamma: number): ColorSpaceManager

Creates a custom color space object that is sendable.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Parameters**

| Name          | Type                                      | Mandatory| Description                         |
| --------------- | ------------------------------------------ | ---- | -----------------------------|
| primaries       | [colorSpaceManager.ColorSpacePrimaries](js-apis-colorSpaceManager.md#colorspaceprimaries)| Yes  | Primaries of the color space.              |
| gamma           | number                                     | Yes  | Gamma value of the color space, which is a floating point number greater than 0.|

**Return value**

| Type               | Description                    |
| ------------------ | ------------------------ |
| [ColorSpaceManager](#colorspacemanager)  | Sendable color space object created.<br>The color space type is **CUSTOM**, which is one of the enumerated values of [colorSpaceManager.ColorSpace](js-apis-colorSpaceManager.md#colorspace).<br>This instance inherits from **ISendable** and can be passed by reference between concurrent ArkTS instances (including the main thread and the worker threads of TaskPool or Worker). For details, see [Using Sendable Objects](../../arkts-utils/sendable-guide.md).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [colorSpaceManager Error Codes](errorcode-colorspace-manager.md).

| ID| Error Message|
| ------- | ----------------------- |
| 401 | Parameter error. Possible cause: 1. Incorrect parameter type. 2. Parameter verification failed.|
| 18600001 | The parameter value is abnormal. |

**Example**

```ts
import { colorSpaceManager, sendableColorSpaceManager } from '@kit.ArkGraphics2D';
let colorSpace: sendableColorSpaceManager.ColorSpaceManager;
// Define the color space criterion primary colors parameter.
let primaries: colorSpaceManager.ColorSpacePrimaries = {
  redX: 0.1,
  redY: 0.1,
  greenX: 0.2,
  greenY: 0.2,
  blueX: 0.3,
  blueY: 0.3,
  whitePointX: 0.4,
  whitePointY: 0.4
};
// Define the color space gamma value.
let gamma: number = 2.2;
// Create a custom color space management instance that is sendable.
colorSpace = sendableColorSpaceManager.create(primaries, gamma);
```

## ColorSpaceManager

Implements management of color space objects. ColorSpaceManager is a core class used to manage and operate color space objects. It provides functions such as obtaining the color space type, white point value, and gamma value, and supports transfer between concurrent ArkTS instances.

Before calling any of the following APIs, you must use [create()](#sendablecolorspacemanagercreate) to create a color space manager.

### getColorSpaceName

getColorSpaceName(): colorSpaceManager.ColorSpace

Obtains the color space type.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Return value**

| Type               | Description                    |
| ------------------ | ------------------------ |
| [colorSpaceManager.ColorSpace](js-apis-colorSpaceManager.md#colorspace)  | Color space type.|

**Error codes**

For details about the error codes, see [colorSpaceManager Error Codes](errorcode-colorspace-manager.md).

| ID| Error Message| 
| ------- | ----------------------- | 
| 18600001 | The parameter value is abnormal. <br>Applicable versions: 12-22|

**Example**

```ts
// Obtain the color space type.
let spaceName: colorSpaceManager.ColorSpace = colorSpace.getColorSpaceName();
```

### getWhitePoint

getWhitePoint(): collections.Array\<number\>

Obtains the white point value of the color space. The chromaticity coordinates [x, y] are returned, indicating the coordinates of the white point in the color space.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Return value**

| Type               | Description                    |
| ------------------ | ------------------------ |
| [collections.Array](../apis-arkts/arkts-apis-arkts-collections-Array.md)\<number>  | Coordinates [x, y] of the white point.|

**Error codes**

For details about the error codes, see [colorSpaceManager Error Codes](errorcode-colorspace-manager.md).

| ID| Error Message| 
| ------- | ----------------------- | 
| 18600001 | The parameter value is abnormal. <br>Applicable versions: 12-22|

**Example**

```ts
import { collections } from '@kit.ArkTS';
// Obtain the white point value [x, y] of the color space.
let point: collections.Array<number> = colorSpace.getWhitePoint();
```

### getGamma

getGamma(): number

Obtains the gamma of the color space.

**System capability**: SystemCapability.Graphic.Graphic2D.ColorManager.Core

**Return value**

| Type               | Description                    |
| ------------------ | ------------------------ |
| number  | Gamma of the color space.|

**Error codes**

For details about the error codes, see [colorSpaceManager Error Codes](errorcode-colorspace-manager.md).

| ID| Error Message| 
| ------- | ----------------------- | 
| 18600001 | The parameter value is abnormal. <br>Applicable versions: 12-22|

**Example**

```ts
// Obtain the gamma value of the color space.
let gamma: number = colorSpace.getGamma();
```
