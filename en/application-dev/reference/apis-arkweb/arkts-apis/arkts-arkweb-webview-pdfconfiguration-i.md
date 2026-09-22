# PdfConfiguration

```TypeScript
interface PdfConfiguration
```

Input parameter of the [createPdf](arkts-arkweb-webview-webviewcontroller-c.md#createpdf) function.

> **NOTE:** 
> 
> The number of pixels is calculated as follows: Number of pixels = 96 x Number of inches.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## height

```TypeScript
height: number
```

Page Height.

Value range: greater than or equal to 0. If the value is out of range, it is set to 0.

Unit: inch.

Recommended value: A4 paper page height 11.69 inches.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## marginBottom

```TypeScript
marginBottom: number
```

Bottom margin.

The value range is [0.0, half of the page height). If the value is not within the value range, set it to **0.0**.

Unit: inch.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## marginLeft

```TypeScript
marginLeft: number
```

Left margin.

The value range is [0.0, half of the page width). If the value is not within the value range, set it to **0.0**.

Unit: inch.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## marginRight

```TypeScript
marginRight: number
```

Right margin.

The value range is [0.0, half of the page width). If the value is not within the value range, set it to **0.0**.

Unit: inch.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## marginTop

```TypeScript
marginTop: number
```

Top margin.

The value range is [0.0, half of the page height). If the value is not within the value range, set it to **0.0**.

Unit: inch.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## scale

```TypeScript
scale?: number
```

Scale multiple.

The value range is [0.0, 2.0]. If the value is less than 0.0, set it to **0.0**. If the value is greater than 2.0, set it to **2.0**.

Default value: **1.0**

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## shouldPrintBackground

```TypeScript
shouldPrintBackground?: boolean
```

Whether to print the background color. The value **true** means to print the background color, and **false** means the opposite.

Default value: **false**.

**Type:** boolean

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core

## width

```TypeScript
width: number
```

Page Width.

Value range: greater than or equal to 0. If the value is out of range, it is set to 0.

Unit: inch.

Recommended value: A4 paper page width 8.27 inches.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.Web.Webview.Core
