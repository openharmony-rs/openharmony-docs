# PrintPageRange

```TypeScript
interface PrintPageRange
```

Defines the print range.

**Since:** 11

<!--Device-print-interface PrintPageRange--><!--Device-print-interface PrintPageRange-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## endPage

```TypeScript
endPage?: number
```

End page. The default value is the maximum number of pages of the file to be printed.

**Type:** number

**Since:** 11

<!--Device-PrintPageRange-endPage?: int--><!--Device-PrintPageRange-endPage?: int-End-->

**System capability:** SystemCapability.Print.PrintFramework

## pages

```TypeScript
pages?: Array<number>
```

Page range set of the file to print. The default value is empty.

**Type:** Array&lt;number&gt;

**Since:** 11

<!--Device-PrintPageRange-pages?: Array<int>--><!--Device-PrintPageRange-pages?: Array<int>-End-->

**System capability:** SystemCapability.Print.PrintFramework

## startPage

```TypeScript
startPage?: number
```

Start page. The default value is **1**.

**Type:** number

**Since:** 11

<!--Device-PrintPageRange-startPage?: int--><!--Device-PrintPageRange-startPage?: int-End-->

**System capability:** SystemCapability.Print.PrintFramework
