# LogEntry (System API)

```TypeScript
interface LogEntry
```

Defines a **LogEntry** object.

**Since:** 10

<!--Device-logLibrary-interface LogEntry--><!--Device-logLibrary-interface LogEntry-End-->

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## mtime

```TypeScript
mtime: number
```

Time of the last modification to the file. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Type:** number

**Since:** 10

<!--Device-LogEntry-mtime: long--><!--Device-LogEntry-mtime: long-End-->

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Log file name.

**Type:** string

**Since:** 10

<!--Device-LogEntry-name: string--><!--Device-LogEntry-name: string-End-->

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.

## size

```TypeScript
size: number
```

File size, in bytes.

**Type:** number

**Since:** 10

<!--Device-LogEntry-size: long--><!--Device-LogEntry-size: long-End-->

**System capability:** SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API:** This is a system API.
