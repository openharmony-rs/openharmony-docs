# PrinterInformation

Defines the printer information.

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## alias

```TypeScript
alias?: string
```

Printer alias.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## capability

```TypeScript
capability?: PrinterCapabilities
```

Printer capabilities.

**Type:** [PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md)

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## description

```TypeScript
description?: string
```

Printer description.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: string
```

Printer details.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## preferences

```TypeScript
preferences?: PrinterPreferences
```

Printer preferences.

**Type:** [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md)

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

Printer ID.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## printerMake

```TypeScript
printerMake?: string
```

Printer model.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## printerName

```TypeScript
printerName: string
```

Printer name.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## printerStatus

```TypeScript
printerStatus: PrinterStatus
```

Printer state.

**Type:** [PrinterStatus](arkts-basicservices-print-printerstatus-e.md)

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## selectedDriver

```TypeScript
selectedDriver?: PpdInfo
```

Information about the selected driver when adding the printer.

**Type:** [PpdInfo](arkts-basicservices-print-ppdinfo-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

## selectedProtocol

```TypeScript
selectedProtocol?: string
```

Protocol used when adding the printer.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

## uri

```TypeScript
uri?: string
```

Printer URI.

**Type:** string

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework
