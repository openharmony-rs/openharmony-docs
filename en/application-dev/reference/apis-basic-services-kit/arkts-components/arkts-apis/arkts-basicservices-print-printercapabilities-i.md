# PrinterCapabilities

Defines the printer capabilities.

**Since:** 14

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

**System capability:** SystemCapability.Print.PrintFramework

## supportedColorModes

```TypeScript
supportedColorModes: Array<PrintColorMode>
```

List of color modes supported by the printer.

**Type:** Array&lt;[PrintColorMode](arkts-basicservices-print-printcolormode-e.md)&gt;

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## supportedDuplexModes

```TypeScript
supportedDuplexModes: Array<PrintDuplexMode>
```

List of single- and double-sided modes supported by the printer.

**Type:** Array&lt;[PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)&gt;

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## supportedMediaTypes

```TypeScript
supportedMediaTypes?: Array<string>
```

List of paper types supported by the printer.

**Type:** Array&lt;string&gt;

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## supportedOrientations

```TypeScript
supportedOrientations?: Array<PrintOrientationMode>
```

List of print directions supported by the printer.

**Type:** Array&lt;[PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md)&gt;

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## supportedPageSizes

```TypeScript
supportedPageSizes: Array<PrintPageSize>
```

List of paper sizes supported by the printer.

**Type:** Array&lt;[PrintPageSize](arkts-basicservices-print-printpagesize-i.md)&gt;

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## supportedQualities

```TypeScript
supportedQualities?: Array<PrintQuality>
```

List of print quality supported by the printer.

**Type:** Array&lt;[PrintQuality](arkts-basicservices-print-printquality-e.md)&gt;

**Since:** 14

**System capability:** SystemCapability.Print.PrintFramework

## vendorJobAttrAbility

```TypeScript
vendorJobAttrAbility?: string
```

Ability to configure job vendor-specific attributes.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

## vendorPrinterPrefAbility

```TypeScript
vendorPrinterPrefAbility?: string
```

Ability to configure printer vendor-specific preferences.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework
