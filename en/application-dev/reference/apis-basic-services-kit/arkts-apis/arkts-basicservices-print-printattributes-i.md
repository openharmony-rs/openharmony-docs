# PrintAttributes

```TypeScript
interface PrintAttributes
```

Defines the print attributes.

**Since:** 11

<!--Device-print-interface PrintAttributes--><!--Device-print-interface PrintAttributes-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## colorMode

```TypeScript
colorMode?: PrintColorMode
```

Color mode of the files to print. If no value is passed, **0** is used by default.

**Type:** [PrintColorMode](arkts-basicservices-print-printcolormode-e.md)

**Since:** 11

<!--Device-PrintAttributes-colorMode?: PrintColorMode--><!--Device-PrintAttributes-colorMode?: PrintColorMode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber?: number
```

Number of printed file copies. The value must be a positive integer. If no value is passed, **0** is used by default.

**Type:** number

**Since:** 11

<!--Device-PrintAttributes-copyNumber?: int--><!--Device-PrintAttributes-copyNumber?: int-End-->

**System capability:** SystemCapability.Print.PrintFramework

## directionMode

```TypeScript
directionMode?: PrintDirectionMode
```

Print direction mode. If no value is passed, **0** is used by default.

**Type:** [PrintDirectionMode](arkts-basicservices-print-printdirectionmode-e.md)

**Since:** 11

<!--Device-PrintAttributes-directionMode?: PrintDirectionMode--><!--Device-PrintAttributes-directionMode?: PrintDirectionMode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode?: PrintDuplexMode
```

Duplex mode of the files to print. If no value is passed, **0** is used by default.

**Type:** [PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)

**Since:** 11

<!--Device-PrintAttributes-duplexMode?: PrintDuplexMode--><!--Device-PrintAttributes-duplexMode?: PrintDuplexMode-End-->

**System capability:** SystemCapability.Print.PrintFramework

## pageRange

```TypeScript
pageRange?: PrintPageRange
```

Page range of the file to print. If no value is passed, the default value is an empty range object.

**Type:** [PrintPageRange](arkts-basicservices-print-printpagerange-i.md)

**Since:** 11

<!--Device-PrintAttributes-pageRange?: PrintPageRange--><!--Device-PrintAttributes-pageRange?: PrintPageRange-End-->

**System capability:** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize?: PrintPageSize | PrintPageType
```

Paper size of the file to print. If no value is passed, the default value is an empty paper size object.

**Type:** [PrintPageSize](arkts-basicservices-print-printpagesize-i.md) &#124; [PrintPageType](arkts-basicservices-print-printpagetype-e.md)

**Since:** 11

<!--Device-PrintAttributes-pageSize?: PrintPageSize | PrintPageType--><!--Device-PrintAttributes-pageSize?: PrintPageSize | PrintPageType-End-->

**System capability:** SystemCapability.Print.PrintFramework
