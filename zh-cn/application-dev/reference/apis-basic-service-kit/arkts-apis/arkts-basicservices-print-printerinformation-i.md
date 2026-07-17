# PrinterInformation

定义打印机信息的接口。

**起始版本：** 14

<!--Device-print-interface PrinterInformation--><!--Device-print-interface PrinterInformation-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## alias

```TypeScript
alias?: string
```

表示打印机别名。

**类型：** string

**起始版本：** 18

<!--Device-PrinterInformation-alias?: string--><!--Device-PrinterInformation-alias?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## capability

```TypeScript
capability?: PrinterCapabilities
```

表示打印机能力。

**类型：** PrinterCapabilities

**起始版本：** 14

<!--Device-PrinterInformation-capability?: PrinterCapabilities--><!--Device-PrinterInformation-capability?: PrinterCapabilities-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## description

```TypeScript
description?: string
```

表示打印机说明。

**类型：** string

**起始版本：** 14

<!--Device-PrinterInformation-description?: string--><!--Device-PrinterInformation-description?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: string
```

表示打印机详细信息。

**类型：** string

**起始版本：** 14

<!--Device-PrinterInformation-options?: string--><!--Device-PrinterInformation-options?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## preferences

```TypeScript
preferences?: PrinterPreferences
```

表示打印机首选项。

**类型：** PrinterPreferences

**起始版本：** 18

<!--Device-PrinterInformation-preferences?: PrinterPreferences--><!--Device-PrinterInformation-preferences?: PrinterPreferences-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## printerId

```TypeScript
printerId: string
```

表示打印机ID。

**类型：** string

**起始版本：** 14

<!--Device-PrinterInformation-printerId: string--><!--Device-PrinterInformation-printerId: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## printerMake

```TypeScript
printerMake?: string
```

表示打印机型号。

**类型：** string

**起始版本：** 14

<!--Device-PrinterInformation-printerMake?: string--><!--Device-PrinterInformation-printerMake?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## printerName

```TypeScript
printerName: string
```

表示打印机名称。

**类型：** string

**起始版本：** 14

<!--Device-PrinterInformation-printerName: string--><!--Device-PrinterInformation-printerName: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## printerStatus

```TypeScript
printerStatus: PrinterStatus
```

表示当前打印机状态。

**类型：** PrinterStatus

**起始版本：** 14

<!--Device-PrinterInformation-printerStatus: PrinterStatus--><!--Device-PrinterInformation-printerStatus: PrinterStatus-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## selectedDriver

```TypeScript
selectedDriver?: PpdInfo
```

表示添加打印机时选择的驱动的信息。

**模型约束：** 此接口仅可在Stage模型下使用。

**类型：** PpdInfo

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrinterInformation-selectedDriver?: PpdInfo--><!--Device-PrinterInformation-selectedDriver?: PpdInfo-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## selectedProtocol

```TypeScript
selectedProtocol?: string
```

表示添加打印机时使用的协议。

**模型约束：** 此接口仅可在Stage模型下使用。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrinterInformation-selectedProtocol?: string--><!--Device-PrinterInformation-selectedProtocol?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## uri

```TypeScript
uri?: string
```

表示打印机uri。

**类型：** string

**起始版本：** 14

<!--Device-PrinterInformation-uri?: string--><!--Device-PrinterInformation-uri?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

