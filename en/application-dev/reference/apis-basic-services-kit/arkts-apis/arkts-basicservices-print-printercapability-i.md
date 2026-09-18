# PrinterCapability

Defines the printer capabilities.

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

## duplexMode

```TypeScript
duplexMode: number
```

Simplex or duplex mode.

**Type:** number

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## minMargin

```TypeScript
minMargin?: PrintMargin
```

Minimum margin of the printer.

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

## pageSize

```TypeScript
pageSize: Array<PrintPageSize>
```

List of page sizes supported by the printer.

**Type:** Array&lt;[PrintPageSize](arkts-basicservices-print-printpagesize-i.md)&gt;

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework

## resolution

```TypeScript
resolution?: Array<PrintResolution>
```

List of resolutions supported by the printer.

**Type:** Array&lt;[PrintResolution](arkts-basicservices-print-printresolution-i.md)&gt;

**Since:** 24

**System capability:** SystemCapability.Print.PrintFramework
