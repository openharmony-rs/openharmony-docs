# PrintJobData

定义打印任务的接口。

**起始版本：** 23

**系统能力：** SystemCapability.Print.PrintFramework

## binaryData

```TypeScript
binaryData?: Uint8Array
```

表示待打印二进制数据。

**类型：** Uint8Array

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## colorMode

```TypeScript
colorMode: PrintColorMode
```

表示色彩模式。

**类型：** PrintColorMode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## copyNumber

```TypeScript
copyNumber: number
```

表示文件列表副本数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## docFlavor

```TypeScript
docFlavor: DocFlavor
```

表示打印数据来源形式。

**类型：** DocFlavor

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## documentFormat

```TypeScript
documentFormat: PrintDocumentFormat
```

表示打印数据格式。

**类型：** PrintDocumentFormat

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: PrintDuplexMode
```

表示单双面打印模式。

**类型：** PrintDuplexMode

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## fdList

```TypeScript
fdList?: number[]
```

表示待打印文件fd列表。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## isAutoRotate

```TypeScript
isAutoRotate?: boolean
```

表示是否自动旋转页面。true表示自动旋转页面，false表示不自动旋转页面。默认值为true。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## isBorderless

```TypeScript
isBorderless?: boolean
```

表示是否无边框打印。true表示无边框打印，false表示有边框打印。默认值为true。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## isCollate

```TypeScript
isCollate?: boolean
```

表示打印顺序方式。true表示逐页打印，false表示逐份打印。默认值为true。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## isLandscape

```TypeScript
isLandscape: boolean
```

表示是否横向打印。true表示横向打印，false表示纵向打印。默认值为false。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## isReverse

```TypeScript
isReverse?: boolean
```

表示是否逆序打印。true表示逆序打印，false表示顺序打印。默认值为false。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## isSequential

```TypeScript
isSequential?: boolean
```

表示是否连续打印。true表示连续打印，false表示不连续打印。默认值为false。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## jobId

```TypeScript
jobId?: string
```

表示打印任务的唯一标识符。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## jobName

```TypeScript
jobName: string
```

表示打印任务名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## mediaType

```TypeScript
mediaType?: string
```

表示打印纸张类型。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: string
```

表示以JSON格式字符串化的对象。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: PrintPageSize
```

表示选定的页面尺寸。

**类型：** PrintPageSize

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## printQuality

```TypeScript
printQuality?: PrintQuality
```

表示打印质量。

**类型：** PrintQuality

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

表示打印机ID。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Print.PrintFramework

