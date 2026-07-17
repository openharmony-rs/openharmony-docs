# PrinterCapability（系统接口）

定义打印能力的接口。

**起始版本：** 24

<!--Device-print-interface PrinterCapability--><!--Device-print-interface PrinterCapability-End-->

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

<!--Device-PrinterCapability-colorMode: int--><!--Device-PrinterCapability-colorMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## duplexMode

```TypeScript
duplexMode: number
```

表示单双面打印模式。

**类型：** number

**起始版本：** 24

<!--Device-PrinterCapability-duplexMode: int--><!--Device-PrinterCapability-duplexMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## minMargin

```TypeScript
minMargin?: PrintMargin
```

表示打印机最小边距。

**类型：** PrintMargin

**起始版本：** 24

<!--Device-PrinterCapability-minMargin?: PrintMargin--><!--Device-PrinterCapability-minMargin?: PrintMargin-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## options

```TypeScript
options?: Object
```

表示JSON对象字符串。

**类型：** Object

**起始版本：** 24

<!--Device-PrinterCapability-options?: Object--><!--Device-PrinterCapability-options?: Object-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## pageSize

```TypeScript
pageSize: Array<PrintPageSize>
```

表示打印机支持的页面尺寸列表。

**类型：** Array<PrintPageSize>

**起始版本：** 24

<!--Device-PrinterCapability-pageSize: Array<PrintPageSize>--><!--Device-PrinterCapability-pageSize: Array<PrintPageSize>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

## resolution

```TypeScript
resolution?: Array<PrintResolution>
```

表示打印机支持的分辨率列表。

**类型：** Array<PrintResolution>

**起始版本：** 24

<!--Device-PrinterCapability-resolution?: Array<PrintResolution>--><!--Device-PrinterCapability-resolution?: Array<PrintResolution>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

**系统接口：** 此接口为系统接口。

