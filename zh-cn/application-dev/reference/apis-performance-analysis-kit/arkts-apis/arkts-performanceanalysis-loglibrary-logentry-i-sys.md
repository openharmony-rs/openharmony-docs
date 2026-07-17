# LogEntry（系统接口）

日志文件对象接口。

**起始版本：** 10

<!--Device-logLibrary-interface LogEntry--><!--Device-logLibrary-interface LogEntry-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## mtime

```TypeScript
mtime: number
```

上次修改该文件的时间，表示距1970年1月1日0时0分0秒的秒数。

**类型：** number

**起始版本：** 10

<!--Device-LogEntry-mtime: long--><!--Device-LogEntry-mtime: long-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

文件名称。

**类型：** string

**起始版本：** 10

<!--Device-LogEntry-name: string--><!--Device-LogEntry-name: string-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

文件大小，以字节为单位。

**类型：** number

**起始版本：** 10

<!--Device-LogEntry-size: long--><!--Device-LogEntry-size: long-End-->

**系统能力：** SystemCapability.HiviewDFX.Hiview.LogLibrary

**系统接口：** 此接口为系统接口。

