# PrintJob（系统接口）

定义打印任务的接口。

**起始版本：** 24

<!--Device-print-interface PrintJob--><!--Device-print-interface PrintJob-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

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

<!--Device-PrintJob-colorMode: int--><!--Device-PrintJob-colorMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## copyNumber

```TypeScript
copyNumber: number
```

表示文件列表副本。

**类型：** number

**起始版本：** 24

<!--Device-PrintJob-copyNumber: int--><!--Device-PrintJob-copyNumber: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## duplexMode

```TypeScript
duplexMode: number
```

表示单双面打印模式。

**类型：** number

**起始版本：** 24

<!--Device-PrintJob-duplexMode: int--><!--Device-PrintJob-duplexMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## fdList

```TypeScript
fdList: Array<number>
```

表示待打印文件fd列表。

**类型：** Array&lt;number&gt;

**起始版本：** 24

<!--Device-PrintJob-fdList: Array<int>--><!--Device-PrintJob-fdList: Array<int>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## isLandscape

```TypeScript
isLandscape: boolean
```

表示是否横向打印。true表示横向打印，false表示纵向打印。默认值为false。

**类型：** boolean

**起始版本：** 24

<!--Device-PrintJob-isLandscape: boolean--><!--Device-PrintJob-isLandscape: boolean-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## isSequential

```TypeScript
isSequential: boolean
```

表示是否连续打印。true表示连续打印，false表示不连续打印。默认值为false。

**类型：** boolean

**起始版本：** 24

<!--Device-PrintJob-isSequential: boolean--><!--Device-PrintJob-isSequential: boolean-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## jobId

```TypeScript
jobId: string
```

表示打印任务ID。

**类型：** string

**起始版本：** 24

<!--Device-PrintJob-jobId: string--><!--Device-PrintJob-jobId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## jobState

```TypeScript
jobState: PrintJobState
```

表示当前打印任务状态。

**类型：** PrintJobState

**起始版本：** 24

<!--Device-PrintJob-jobState: PrintJobState--><!--Device-PrintJob-jobState: PrintJobState-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## jobSubstate

```TypeScript
jobSubstate: PrintJobSubState
```

表示当前打印任务子状态。

**类型：** PrintJobSubState

**起始版本：** 24

<!--Device-PrintJob-jobSubstate: PrintJobSubState--><!--Device-PrintJob-jobSubstate: PrintJobSubState-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## margin

```TypeScript
margin?: PrintMargin
```

表示当前页边距设置。

**类型：** PrintMargin

**起始版本：** 24

<!--Device-PrintJob-margin?: PrintMargin--><!--Device-PrintJob-margin?: PrintMargin-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## options

```TypeScript
options?: Object
```

表示JSON对象字符串。

**类型：** Object

**起始版本：** 24

<!--Device-PrintJob-options?: Object--><!--Device-PrintJob-options?: Object-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## pageRange

```TypeScript
pageRange: PrinterRange
```

表示打印范围大小。

**类型：** PrinterRange

**起始版本：** 24

<!--Device-PrintJob-pageRange: PrinterRange--><!--Device-PrintJob-pageRange: PrinterRange-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## pageSize

```TypeScript
pageSize: PrintPageSize
```

表示选定的页面尺寸。

**类型：** PrintPageSize

**起始版本：** 24

<!--Device-PrintJob-pageSize: PrintPageSize--><!--Device-PrintJob-pageSize: PrintPageSize-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## preview

```TypeScript
preview?: PreviewAttribute
```

表示预览设置。

**类型：** PreviewAttribute

**起始版本：** 24

<!--Device-PrintJob-preview?: PreviewAttribute--><!--Device-PrintJob-preview?: PreviewAttribute-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## printerId

```TypeScript
printerId: string
```

表示负责打印的打印机ID。

**类型：** string

**起始版本：** 24

<!--Device-PrintJob-printerId: string--><!--Device-PrintJob-printerId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

