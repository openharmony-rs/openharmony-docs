# PrintJob

Defines a print job.

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## colorMode

```TypeScript
colorMode: number
```

Color mode.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber: number
```

Copy of the file list.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: number
```

Simplex or duplex mode.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## fdList

```TypeScript
fdList: Array<number>
```

FD list of files to print.

**Type:** Array&lt;number&gt;

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## isLandscape

```TypeScript
isLandscape: boolean
```

Whether pages are printed in landscape mode. The value **true** indicates that pages are printed in landscape mode, and **false** indicates that pages are printed in portrait mode. The default value is **false**.

**Type:** boolean

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## isSequential

```TypeScript
isSequential: boolean
```

Whether the printing is sequential. The value **true** means that the printing is sequential, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## jobId

```TypeScript
jobId: string
```

ID of the print job.

**Type:** string

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## jobState

```TypeScript
jobState: PrintJobState
```

State of the print job.

**Type:** [PrintJobState](arkts-basicservices-print-printjobstate-e.md)

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## jobSubstate

```TypeScript
jobSubstate: PrintJobSubState
```

Substate of the print job.

**Type:** [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md)

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## margin

```TypeScript
margin?: PrintMargin
```

Current page margin.

**Type:** [PrintMargin](arkts-basicservices-print-printmargin-i.md)

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: Object
```

Printer options. The value is a JSON object string.

**Type:** Object

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## pageRange

```TypeScript
pageRange: PrinterRange
```

Print range.

**Type:** [PrinterRange](arkts-basicservices-print-printerrange-i.md)

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: PrintPageSize
```

Selected page size.

**Type:** [PrintPageSize](arkts-basicservices-print-printpagesize-i.md)

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## preview

```TypeScript
preview?: PreviewAttribute
```

Preview settings.

**Type:** [PreviewAttribute](arkts-basicservices-print-previewattribute-i.md)

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

ID of the printer used for printing.

**Type:** string

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## vendorOptions

```TypeScript
vendorOptions?: string
```

Vendor-specific job options in JSON format.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework
