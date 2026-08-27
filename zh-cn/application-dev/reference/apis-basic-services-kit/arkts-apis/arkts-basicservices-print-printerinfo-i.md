# PrinterInfo

定义打印信息的接口。

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## capability

```TypeScript
capability?: PrinterCapability
```

表示打印机功能。

**类型：** [PrinterCapability](arkts-basicservices-print-printercapability-i.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## description

```TypeScript
description?: string
```

表示打印机说明。

**类型：** string

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

## printerIcon

```TypeScript
printerIcon?: number
```

表示打印机图标的资源ID。默认值为-1。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

表示打印机ID。

**类型：** string

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## printerName

```TypeScript
printerName: string
```

表示打印机名称。

**类型：** string

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## printerState

```TypeScript
printerState: PrinterState
```

表示当前打印机状态。

**类型：** [PrinterState](arkts-basicservices-print-printerstate-e.md)

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework
