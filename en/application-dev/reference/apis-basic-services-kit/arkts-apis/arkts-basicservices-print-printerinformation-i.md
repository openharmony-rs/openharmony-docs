# PrinterInformation

```TypeScript
interface PrinterInformation
```

Defines the printer information.

**Since:** 14

<!--Device-print-interface PrinterInformation--><!--Device-print-interface PrinterInformation-End-->

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

<!--Device-PrinterInformation-alias?: string--><!--Device-PrinterInformation-alias?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## capability

```TypeScript
capability?: PrinterCapabilities
```

Printer capabilities.

**Type:** [PrinterCapabilities](arkts-basicservices-print-printercapabilities-i.md)

**Since:** 14

<!--Device-PrinterInformation-capability?: PrinterCapabilities--><!--Device-PrinterInformation-capability?: PrinterCapabilities-End-->

**System capability:** SystemCapability.Print.PrintFramework

## description

```TypeScript
description?: string
```

Printer description.

**Type:** string

**Since:** 14

<!--Device-PrinterInformation-description?: string--><!--Device-PrinterInformation-description?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: string
```

Printer details.

**Type:** string

**Since:** 14

<!--Device-PrinterInformation-options?: string--><!--Device-PrinterInformation-options?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## preferences

```TypeScript
preferences?: PrinterPreferences
```

Printer preferences.

**Type:** [PrinterPreferences](arkts-basicservices-print-printerpreferences-i.md)

**Since:** 18

<!--Device-PrinterInformation-preferences?: PrinterPreferences--><!--Device-PrinterInformation-preferences?: PrinterPreferences-End-->

**System capability:** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

Printer ID.

**Type:** string

**Since:** 14

<!--Device-PrinterInformation-printerId: string--><!--Device-PrinterInformation-printerId: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## printerMake

```TypeScript
printerMake?: string
```

Printer model.

**Type:** string

**Since:** 14

<!--Device-PrinterInformation-printerMake?: string--><!--Device-PrinterInformation-printerMake?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## printerName

```TypeScript
printerName: string
```

Printer name.

**Type:** string

**Since:** 14

<!--Device-PrinterInformation-printerName: string--><!--Device-PrinterInformation-printerName: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## printerStatus

```TypeScript
printerStatus: PrinterStatus
```

Printer state.

**Type:** [PrinterStatus](arkts-basicservices-print-printerstatus-e.md)

**Since:** 14

<!--Device-PrinterInformation-printerStatus: PrinterStatus--><!--Device-PrinterInformation-printerStatus: PrinterStatus-End-->

**System capability:** SystemCapability.Print.PrintFramework

## selectedDriver

```TypeScript
selectedDriver?: PpdInfo
```

Information about the selected driver when adding the printer.

**Type:** [PpdInfo](arkts-basicservices-print-ppdinfo-i.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrinterInformation-selectedDriver?: PpdInfo--><!--Device-PrinterInformation-selectedDriver?: PpdInfo-End-->

**System capability:** SystemCapability.Print.PrintFramework

## selectedProtocol

```TypeScript
selectedProtocol?: string
```

Protocol used when adding the printer.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrinterInformation-selectedProtocol?: string--><!--Device-PrinterInformation-selectedProtocol?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## uri

```TypeScript
uri?: string
```

Printer URI.

**Type:** string

**Since:** 14

<!--Device-PrinterInformation-uri?: string--><!--Device-PrinterInformation-uri?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework
