# PrintAttributes

Defines the print attributes.

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## colorMode

```TypeScript
colorMode?: PrintColorMode
```

Color mode of the files to print.

**Type:** [PrintColorMode](arkts-basicservices-print-printcolormode-e.md)

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber?: number
```

Number of printed file copies. The default value is **1**.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework

## directionMode

```TypeScript
directionMode?: PrintDirectionMode
```

Print direction mode.

**Type:** [PrintDirectionMode](arkts-basicservices-print-printdirectionmode-e.md)

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode?: PrintDuplexMode
```

Duplex mode of the files to print.

**Type:** [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework

## pageRange

```TypeScript
pageRange?: PrintPageRange
```

Page range of the file to print.

**Type:** [PrintPageRange](arkts-basicservices-print-printpagerange-i.md)

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize?: PrintPageSize | PrintPageType
```

Page size of the file to print.

**Type:** [PrintPageSize](arkts-basicservices-print-printpagesize-i.md) &#124; [PrintPageType](arkts-basicservices-print-printpagetype-e.md)

**Since:** 11

**System capability:** SystemCapability.Print.PrintFramework
