# PictureScanProgress

Defines the progress of scanning pictures.

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## Modules to Import

```TypeScript
import { scan } from '@kit.BasicServicesKit';
```

## isFinal

```TypeScript
isFinal: boolean
```

Whether the picture is the last one to be scanned. The value **true** indicates that the picture is the last one to be scanned, and **false** indicates that the picture is not the last one.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## pictureFd

```TypeScript
pictureFd: number
```

File descriptor of the scanned picture.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework

## progress

```TypeScript
progress: number
```

Progress percentage, whose value ranges from 0 to 100. Unit: %

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Print.PrintFramework
