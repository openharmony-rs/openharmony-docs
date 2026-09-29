# PrinterCapability

```TypeScript
interface PrinterCapability
```

Defines the printer capabilities.

**Since:** 24

<!--Device-print-interface PrinterCapability--><!--Device-print-interface PrinterCapability-End-->

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

<!--Device-PrinterCapability-colorMode: int--><!--Device-PrinterCapability-colorMode: int-End-->

**System capability:** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: number
```

Simplex or duplex mode.

**Type:** number

**Since:** 24

<!--Device-PrinterCapability-duplexMode: int--><!--Device-PrinterCapability-duplexMode: int-End-->

**System capability:** SystemCapability.Print.PrintFramework

## minMargin

```TypeScript
minMargin?: PrintMargin
```

Minimum margin of the printer.

**Type:** [PrintMargin](arkts-basicservices-print-printmargin-i.md)

**Since:** 24

<!--Device-PrinterCapability-minMargin?: PrintMargin--><!--Device-PrinterCapability-minMargin?: PrintMargin-End-->

**System capability:** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: Object
```

Printer options. The value is a JSON object string.

**Type:** Object

**Since:** 24

<!--Device-PrinterCapability-options?: Object--><!--Device-PrinterCapability-options?: Object-End-->

**System capability:** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: Array<PrintPageSize>
```

List of page sizes supported by the printer.

**Type:** Array&lt;[PrintPageSize](arkts-basicservices-print-printpagesize-i.md)&gt;

**Since:** 24

<!--Device-PrinterCapability-pageSize: Array<PrintPageSize>--><!--Device-PrinterCapability-pageSize: Array<PrintPageSize>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## resolution

```TypeScript
resolution?: Array<PrintResolution>
```

List of resolutions supported by the printer.

**Type:** Array&lt;[PrintResolution](arkts-basicservices-print-printresolution-i.md)&gt;

**Since:** 24

<!--Device-PrinterCapability-resolution?: Array<PrintResolution>--><!--Device-PrinterCapability-resolution?: Array<PrintResolution>-End-->

**System capability:** SystemCapability.Print.PrintFramework
