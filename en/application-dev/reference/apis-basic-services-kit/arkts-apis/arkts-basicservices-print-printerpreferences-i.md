# PrinterPreferences

Defines the printer preferences.

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## borderless

```TypeScript
borderless?: boolean
```

Whether to print without margins. The value **true** means to print without margins, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## defaultCollate

```TypeScript
defaultCollate?: boolean
```

Default collate.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

## defaultColorMode

```TypeScript
defaultColorMode?: PrintColorMode
```

Default color mode.

**Type:** [PrintColorMode](arkts-basicservices-print-printcolormode-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

## defaultDuplexMode

```TypeScript
defaultDuplexMode?: PrintDuplexMode
```

Default duplex mode.

**Type:** [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## defaultMediaType

```TypeScript
defaultMediaType?: string
```

Default paper type.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## defaultOrientation

```TypeScript
defaultOrientation?: PrintOrientationMode
```

Default print orientation.

**Type:** [PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md)

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## defaultPageSizeId

```TypeScript
defaultPageSizeId?: string
```

ID of the default paper size. The value can be a standard paper size defined by the International Organization for Standardization (ISO), for example, ISO_A4, or a non-standard paper size defined in the system, for example, Custom.178 × 254 mm.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## defaultPrintQuality

```TypeScript
defaultPrintQuality?: PrintQuality
```

Default print quality.

**Type:** [PrintQuality](arkts-basicservices-print-printquality-e.md)

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## defaultReverse

```TypeScript
defaultReverse?: boolean
```

Default reverse.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: string
```

Other fields in the printer preferences. The fields are queried from the printer or obtained from the printer driver and stored in the string in JSON format.

**Type:** string

**Since:** 18

**System capability:** SystemCapability.Print.PrintFramework

## vendorOptions

```TypeScript
vendorOptions?: string
```

Vendor-specific printer preferences in JSON format.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Print.PrintFramework
