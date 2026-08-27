# PrintJob

定义打印任务的接口。

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## colorMode

```TypeScript
colorMode: number
```

表示色彩模式。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber: number
```

表示文件列表副本。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: number
```

表示单双面打印模式。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## fdList

```TypeScript
fdList: Array<number>
```

表示待打印文件fd列表。

**类型：** Array&lt;number&gt;

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## isLandscape

```TypeScript
isLandscape: boolean
```

表示是否横向打印。true表示横向打印，false表示纵向打印。默认值为false。

**类型：** boolean

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## isSequential

```TypeScript
isSequential: boolean
```

表示是否连续打印。true表示连续打印，false表示不连续打印。默认值为false。

**类型：** boolean

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## jobId

```TypeScript
jobId: string
```

表示打印任务ID。

**类型：** string

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## jobState

```TypeScript
jobState: PrintJobState
```

表示当前打印任务状态。

**类型：** [PrintJobState](arkts-basicservices-print-printjobstate-e.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## jobSubstate

```TypeScript
jobSubstate: PrintJobSubState
```

表示当前打印任务子状态。

**类型：** [PrintJobSubState](arkts-basicservices-print-printjobsubstate-e.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## margin

```TypeScript
margin?: PrintMargin
```

表示当前页边距设置。

**类型：** [PrintMargin](arkts-basicservices-print-printmargin-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: Object
```

表示JSON对象字符串。

**类型：** Object

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## pageRange

```TypeScript
pageRange: PrinterRange
```

表示打印范围大小。

**类型：** [PrinterRange](arkts-basicservices-print-printerrange-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: PrintPageSize
```

表示选定的页面尺寸。

**类型：** [PrintPageSize](arkts-basicservices-print-printpagesize-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## preview

```TypeScript
preview?: PreviewAttribute
```

表示预览设置。

**类型：** [PreviewAttribute](arkts-basicservices-print-previewattribute-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

表示负责打印的打印机ID。

**类型：** string

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework
