# PrintJobData

```TypeScript
interface PrintJobData
```

Defines a print job.

**Since:** 23

<!--Device-print-interface PrintJobData--><!--Device-print-interface PrintJobData-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## binaryData

```TypeScript
binaryData?: Uint8Array
```

Binary data to print.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-binaryData?: Uint8Array--><!--Device-PrintJobData-binaryData?: Uint8Array-End-->

**System capability:** SystemCapability.Print.PrintFramework

## colorMode

```TypeScript
colorMode: PrintColorMode
```

Color mode.

**Type:** [PrintColorMode](arkts-basicservices-print-printcolormode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-colorMode: PrintColorMode--><!--Device-PrintJobData-colorMode: PrintColorMode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber: number
```

Number of file list copies.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-copyNumber: int--><!--Device-PrintJobData-copyNumber: int-End-->

**System capability:** SystemCapability.Print.PrintFramework

## docFlavor

```TypeScript
docFlavor: DocFlavor
```

Data source type.

**Type:** [DocFlavor](arkts-basicservices-print-docflavor-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-docFlavor: DocFlavor--><!--Device-PrintJobData-docFlavor: DocFlavor-End-->

**System capability:** SystemCapability.Print.PrintFramework

## documentFormat

```TypeScript
documentFormat: PrintDocumentFormat
```

Format of the print data.

**Type:** [PrintDocumentFormat](arkts-basicservices-print-printdocumentformat-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-documentFormat: PrintDocumentFormat--><!--Device-PrintJobData-documentFormat: PrintDocumentFormat-End-->

**System capability:** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: PrintDuplexMode
```

Simplex or duplex mode.

**Type:** [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-duplexMode: PrintDuplexMode--><!--Device-PrintJobData-duplexMode: PrintDuplexMode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## fdList

```TypeScript
fdList?: number[]
```

FD list of files to print.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-fdList?: int[]--><!--Device-PrintJobData-fdList?: int[]-End-->

**System capability:** SystemCapability.Print.PrintFramework

## isAutoRotate

```TypeScript
isAutoRotate?: boolean
```

Whether to automatically rotate the page. The value **true** means to automatically rotate the page, and **false** means the opposite. Default value: **true**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-isAutoRotate?: boolean--><!--Device-PrintJobData-isAutoRotate?: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## isBorderless

```TypeScript
isBorderless?: boolean
```

Whether to print without margins. The value **true** means to print without margins, and **false** means the opposite. Default value: **true**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-isBorderless?: boolean--><!--Device-PrintJobData-isBorderless?: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## isCollate

```TypeScript
isCollate?: boolean
```

Whether pages are printed uncollated. The value **true** means that pages are printed uncollated, and **false** means the opposite. Default value: **true**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-isCollate?: boolean--><!--Device-PrintJobData-isCollate?: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## isLandscape

```TypeScript
isLandscape: boolean
```

Whether pages are printed in landscape mode. The value **true** indicates that pages are printed in landscape mode, and **false** indicates that pages are printed in portrait mode. The default value is **false**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-isLandscape: boolean--><!--Device-PrintJobData-isLandscape: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## isReverse

```TypeScript
isReverse?: boolean
```

Whether pages are printed in reverse order. The value **true** means that pages are printed in reverse order, and **false** means that pages are printed in normal order. The default value is **false**.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-isReverse?: boolean--><!--Device-PrintJobData-isReverse?: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## isSequential

```TypeScript
isSequential?: boolean
```

Whether pages are printed in sequential order.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-isSequential?: boolean--><!--Device-PrintJobData-isSequential?: boolean-End-->

**System capability:** SystemCapability.Print.PrintFramework

## jobId

```TypeScript
jobId?: string
```

Unique identifier of the print job.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-jobId?: string--><!--Device-PrintJobData-jobId?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## jobName

```TypeScript
jobName: string
```

Name of the print job.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-jobName: string--><!--Device-PrintJobData-jobName: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## mediaType

```TypeScript
mediaType?: string
```

Type of the paper to print.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-mediaType?: string--><!--Device-PrintJobData-mediaType?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: string
```

Object stringified in JSON format.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-options?: string--><!--Device-PrintJobData-options?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: PrintPageSize
```

Selected page size.

**Type:** [PrintPageSize](arkts-basicservices-print-printpagesize-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-pageSize: PrintPageSize--><!--Device-PrintJobData-pageSize: PrintPageSize-End-->

**System capability:** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

Printer ID.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-printerId: string--><!--Device-PrintJobData-printerId: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## printQuality

```TypeScript
printQuality?: PrintQuality
```

Print quality.

**Type:** [PrintQuality](arkts-basicservices-print-printquality-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-printQuality?: PrintQuality--><!--Device-PrintJobData-printQuality?: PrintQuality-End-->

**System capability:** SystemCapability.Print.PrintFramework

## vendorOptions

```TypeScript
vendorOptions?: string
```

Vendor-specific job options in JSON format.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrintJobData-vendorOptions?: string--><!--Device-PrintJobData-vendorOptions?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework
