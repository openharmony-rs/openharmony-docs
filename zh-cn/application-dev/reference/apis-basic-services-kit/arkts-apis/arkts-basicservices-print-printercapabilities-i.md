# PrinterCapabilities

```TypeScript
interface PrinterCapabilities
```

定义打印机能力的接口。

**起始版本：** 14

<!--Device-print-interface PrinterCapabilities--><!--Device-print-interface PrinterCapabilities-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## 导入模块

```TypeScript
import { print } from '@kit.BasicServicesKit';
```

## options

```TypeScript
options?: string
```

表示打印机能力详细信息。不传入时默认值为空字符串。

**类型：** string

**起始版本：** 14

<!--Device-PrinterCapabilities-options?: string--><!--Device-PrinterCapabilities-options?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## supportedColorModes

```TypeScript
supportedColorModes: Array<PrintColorMode>
```

表示打印机支持的色彩模式列表。

**类型：** Array&lt;[PrintColorMode](arkts-basicservices-print-printcolormode-e.md)&gt;

**起始版本：** 14

<!--Device-PrinterCapabilities-supportedColorModes: Array<PrintColorMode>--><!--Device-PrinterCapabilities-supportedColorModes: Array<PrintColorMode>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## supportedDuplexModes

```TypeScript
supportedDuplexModes: Array<PrintDuplexMode>
```

表示打印机支持的单双面模式列表。

**类型：** Array&lt;[PrintDuplexMode](arkts-basicservices-print-printduplexmode-e.md)&gt;

**起始版本：** 14

<!--Device-PrinterCapabilities-supportedDuplexModes: Array<PrintDuplexMode>--><!--Device-PrinterCapabilities-supportedDuplexModes: Array<PrintDuplexMode>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## supportedMediaTypes

```TypeScript
supportedMediaTypes?: Array<string>
```

表示打印机支持的纸张类型列表。不传入时默认值为空列表。

**类型：** Array&lt;string&gt;

**起始版本：** 14

<!--Device-PrinterCapabilities-supportedMediaTypes?: Array<string>--><!--Device-PrinterCapabilities-supportedMediaTypes?: Array<string>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## supportedOrientations

```TypeScript
supportedOrientations?: Array<PrintOrientationMode>
```

表示打印机支持的打印方向列表。不传入时默认值为空列表。

**类型：** Array&lt;[PrintOrientationMode](arkts-basicservices-print-printorientationmode-e.md)&gt;

**起始版本：** 14

<!--Device-PrinterCapabilities-supportedOrientations?: Array<PrintOrientationMode>--><!--Device-PrinterCapabilities-supportedOrientations?: Array<PrintOrientationMode>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## supportedPageSizes

```TypeScript
supportedPageSizes: Array<PrintPageSize>
```

表示打印机支持的纸张尺寸列表。

**类型：** Array&lt;[PrintPageSize](arkts-basicservices-print-printpagesize-i.md)&gt;

**起始版本：** 14

<!--Device-PrinterCapabilities-supportedPageSizes: Array<PrintPageSize>--><!--Device-PrinterCapabilities-supportedPageSizes: Array<PrintPageSize>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## supportedQualities

```TypeScript
supportedQualities?: Array<PrintQuality>
```

表示打印机支持的打印质量列表。不传入时默认值为空列表。

**类型：** Array&lt;[PrintQuality](arkts-basicservices-print-printquality-e.md)&gt;

**起始版本：** 14

<!--Device-PrinterCapabilities-supportedQualities?: Array<PrintQuality>--><!--Device-PrinterCapabilities-supportedQualities?: Array<PrintQuality>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## vendorJobAttrAbility

```TypeScript
vendorJobAttrAbility?: string
```

表示由打印机驱动厂商提供的打印任务属性设置界面。不传入时默认值为空字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrinterCapabilities-vendorJobAttrAbility?: string--><!--Device-PrinterCapabilities-vendorJobAttrAbility?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## vendorPrinterPrefAbility

```TypeScript
vendorPrinterPrefAbility?: string
```

表示由打印机驱动厂商提供的打印机首选项设置界面。不传入时默认值为空字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PrinterCapabilities-vendorPrinterPrefAbility?: string--><!--Device-PrinterCapabilities-vendorPrinterPrefAbility?: string-End-->

**系统能力：** SystemCapability.Print.PrintFramework
