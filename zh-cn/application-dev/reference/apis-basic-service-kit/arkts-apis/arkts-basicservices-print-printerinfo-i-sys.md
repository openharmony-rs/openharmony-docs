# PrinterInfo（系统接口）

定义打印信息的接口。

**起始版本：** 24

<!--Device-print-interface PrinterInfo--><!--Device-print-interface PrinterInfo-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## capability

```TypeScript
capability?: PrinterCapability
```

表示打印机功能。

**类型：** PrinterCapability

**起始版本：** 24

<!--Device-PrinterInfo-capability?: PrinterCapability--><!--Device-PrinterInfo-capability?: PrinterCapability-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## description

```TypeScript
description?: string
```

表示打印机说明。

**类型：** string

**起始版本：** 24

<!--Device-PrinterInfo-description?: string--><!--Device-PrinterInfo-description?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## options

```TypeScript
options?: Object
```

表示JSON对象字符串。

**类型：** Object

**起始版本：** 24

<!--Device-PrinterInfo-options?: Object--><!--Device-PrinterInfo-options?: Object-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## printerIcon

```TypeScript
printerIcon?: number
```

表示打印机图标的资源ID。默认值为-1。

**类型：** number

**起始版本：** 24

<!--Device-PrinterInfo-printerIcon?: int--><!--Device-PrinterInfo-printerIcon?: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## printerId

```TypeScript
printerId: string
```

表示打印机ID。

**类型：** string

**起始版本：** 24

<!--Device-PrinterInfo-printerId: string--><!--Device-PrinterInfo-printerId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## printerName

```TypeScript
printerName: string
```

表示打印机名称。

**类型：** string

**起始版本：** 24

<!--Device-PrinterInfo-printerName: string--><!--Device-PrinterInfo-printerName: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## printerState

```TypeScript
printerState: PrinterState
```

表示当前打印机状态。

**类型：** PrinterState

**起始版本：** 24

<!--Device-PrinterInfo-printerState: PrinterState--><!--Device-PrinterInfo-printerState: PrinterState-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

