# PpdInfo

```TypeScript
interface PpdInfo
```

Defines the PPD file information of the printer driver.

**Since:** 24

<!--Device-print-interface PpdInfo--><!--Device-print-interface PpdInfo-End-->

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## manufacturer

```TypeScript
manufacturer: string
```

Printer vendor name in the current PPD file.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PpdInfo-manufacturer: string--><!--Device-PpdInfo-manufacturer: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## nickName

```TypeScript
nickName: string
```

Printer alias in the current PPD file.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PpdInfo-nickName: string--><!--Device-PpdInfo-nickName: string-End-->

**System capability:** SystemCapability.Print.PrintFramework

## ppdName

```TypeScript
ppdName: string
```

Name of the current PPD file.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-PpdInfo-ppdName: string--><!--Device-PpdInfo-ppdName: string-End-->

**System capability:** SystemCapability.Print.PrintFramework
