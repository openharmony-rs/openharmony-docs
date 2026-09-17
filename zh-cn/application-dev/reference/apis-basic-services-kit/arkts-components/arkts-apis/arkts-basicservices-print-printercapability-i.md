# PrinterCapability

定义打印能力的接口。

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

## duplexMode

```TypeScript
duplexMode: number
```

表示单双面打印模式。

**类型：** number

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## minMargin

```TypeScript
minMargin?: PrintMargin
```

表示打印机最小边距。

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

## pageSize

```TypeScript
pageSize: Array<PrintPageSize>
```

表示打印机支持的页面尺寸列表。

**类型：** Array&lt;[PrintPageSize](arkts-basicservices-print-printpagesize-i.md)&gt;

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework

## resolution

```TypeScript
resolution?: Array<PrintResolution>
```

表示打印机支持的分辨率列表。

**类型：** Array&lt;[PrintResolution](arkts-basicservices-print-printresolution-i.md)&gt;

**起始版本：** 24

**系统能力：** SystemCapability.Print.PrintFramework
