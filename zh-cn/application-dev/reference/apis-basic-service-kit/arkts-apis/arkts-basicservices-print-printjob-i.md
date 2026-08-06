# PrintJob

定义打印任务的接口。

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-print-interface PrintJob--><!--Device-print-interface PrintJob-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## colorMode

```TypeScript
colorMode: int
```

表示色彩模式。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-colorMode: int--><!--Device-PrintJob-colorMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber: int
```

表示文件列表副本。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-copyNumber: int--><!--Device-PrintJob-copyNumber: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: int
```

表示单双面打印模式。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-duplexMode: int--><!--Device-PrintJob-duplexMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## fdList

```TypeScript
fdList: Array<int>
```

表示待打印文件fd列表。

**类型：** Array&lt;int&gt;

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-fdList: Array<int>--><!--Device-PrintJob-fdList: Array<int>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## isLandscape

```TypeScript
isLandscape: boolean
```

表示是否横向打印。true表示横向打印，false表示纵向打印。默认值为false。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-isLandscape: boolean--><!--Device-PrintJob-isLandscape: boolean-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## isSequential

```TypeScript
isSequential: boolean
```

表示是否连续打印。true表示连续打印，false表示不连续打印。默认值为false。

**类型：** boolean

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-isSequential: boolean--><!--Device-PrintJob-isSequential: boolean-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## jobId

```TypeScript
jobId: string
```

表示打印任务ID。

**类型：** string

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-jobId: string--><!--Device-PrintJob-jobId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## jobState

```TypeScript
jobState: PrintJobState
```

表示当前打印任务状态。

**类型：** PrintJobState

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-jobState: PrintJobState--><!--Device-PrintJob-jobState: PrintJobState-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## jobSubstate

```TypeScript
jobSubstate: PrintJobSubState
```

表示当前打印任务子状态。

**类型：** PrintJobSubState

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-jobSubstate: PrintJobSubState--><!--Device-PrintJob-jobSubstate: PrintJobSubState-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## margin

```TypeScript
margin?: PrintMargin
```

表示当前页边距设置。

**类型：** PrintMargin

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-margin?: PrintMargin--><!--Device-PrintJob-margin?: PrintMargin-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: Object
```

表示JSON对象字符串。

**类型：** Object

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-options?: Object--><!--Device-PrintJob-options?: Object-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pageRange

```TypeScript
pageRange: PrinterRange
```

表示打印范围大小。

**类型：** PrinterRange

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-pageRange: PrinterRange--><!--Device-PrintJob-pageRange: PrinterRange-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: PrintPageSize
```

表示选定的页面尺寸。

**类型：** PrintPageSize

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-pageSize: PrintPageSize--><!--Device-PrintJob-pageSize: PrintPageSize-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## preview

```TypeScript
preview?: PreviewAttribute
```

表示预览设置。

**类型：** PreviewAttribute

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-preview?: PreviewAttribute--><!--Device-PrintJob-preview?: PreviewAttribute-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

表示负责打印的打印机ID。

**类型：** string

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrintJob-printerId: string--><!--Device-PrintJob-printerId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

