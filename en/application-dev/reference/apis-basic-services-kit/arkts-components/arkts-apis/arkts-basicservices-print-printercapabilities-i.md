# PrinterCapabilities

```TypeScript
interface PrinterCapabilities
```

Defines the printer capabilities.

**Since:** 14

<!--Device-print-interface PrinterCapabilities--><!--Device-print-interface PrinterCapabilities-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## options

```TypeScript
options?: string
```

Printer capability details.

**Type:** string

**Since:** 14

<!--Device-PrinterCapabilities-options?: string--><!--Device-PrinterCapabilities-options?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## supportedColorModes

```TypeScript
supportedColorModes: Array<PrintColorMode>
```

List of color modes supported by the printer.

**Type:** Array&lt;[PrintColorMode](arkts-basicservices-print-printcolormode-e.md)&gt;

**Since:** 14

<!--Device-PrinterCapabilities-supportedColorModes: Array<PrintColorMode>--><!--Device-PrinterCapabilities-supportedColorModes: Array<PrintColorMode>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## supportedDuplexModes

```TypeScript
supportedDuplexModes: Array<PrintDuplexMode>
```

List of single- and double-sided modes supported by the printer.

**Type:** Array&lt;[PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)&gt;

**Since:** 14

<!--Device-PrinterCapabilities-supportedDuplexModes: Array<PrintDuplexMode>--><!--Device-PrinterCapabilities-supportedDuplexModes: Array<PrintDuplexMode>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## supportedMediaTypes

```TypeScript
supportedMediaTypes?: Array<string>
```

List of paper types supported by the printer.

**Type:** Array&lt;string&gt;

**Since:** 14

<!--Device-PrinterCapabilities-supportedMediaTypes?: Array<string>--><!--Device-PrinterCapabilities-supportedMediaTypes?: Array<string>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## supportedOrientations

```TypeScript
supportedOrientations?: Array<PrintOrientationMode>
```

List of print directions supported by the printer.

**Type:** Array&lt;[PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md)&gt;

**Since:** 14

<!--Device-PrinterCapabilities-supportedOrientations?: Array<PrintOrientationMode>--><!--Device-PrinterCapabilities-supportedOrientations?: Array<PrintOrientationMode>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## supportedPageSizes

```TypeScript
supportedPageSizes: Array<PrintPageSize>
```

List of paper sizes supported by the printer.

**Type:** Array&lt;[PrintPageSize](arkts-basicservices-print-printpagesize-i.md)&gt;

**Since:** 14

<!--Device-PrinterCapabilities-supportedPageSizes: Array<PrintPageSize>--><!--Device-PrinterCapabilities-supportedPageSizes: Array<PrintPageSize>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## supportedQualities

```TypeScript
supportedQualities?: Array<PrintQuality>
```

List of print quality supported by the printer.

**Type:** Array&lt;[PrintQuality](arkts-basicservices-print-printquality-e.md)&gt;

**Since:** 14

<!--Device-PrinterCapabilities-supportedQualities?: Array<PrintQuality>--><!--Device-PrinterCapabilities-supportedQualities?: Array<PrintQuality>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## vendorJobAttrAbility

```TypeScript
vendorJobAttrAbility?: string
```

Ability to configure job vendor-specific attributes.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrinterCapabilities-vendorJobAttrAbility?: string--><!--Device-PrinterCapabilities-vendorJobAttrAbility?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## vendorPrinterPrefAbility

```TypeScript
vendorPrinterPrefAbility?: string
```

Ability to configure printer vendor-specific preferences.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PrinterCapabilities-vendorPrinterPrefAbility?: string--><!--Device-PrinterCapabilities-vendorPrinterPrefAbility?: string-End-->

**System capability:** SystemCapability.Print.PrintFramework
