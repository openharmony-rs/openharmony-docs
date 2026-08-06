# PrinterCapability

定义打印能力的接口。

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-print-interface PrinterCapability--><!--Device-print-interface PrinterCapability-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## colorMode

```TypeScript
colorMode: int
```

表示色彩模式。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterCapability-colorMode: int--><!--Device-PrinterCapability-colorMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## duplexMode

```TypeScript
duplexMode: int
```

表示单双面打印模式。

**类型：** int

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterCapability-duplexMode: int--><!--Device-PrinterCapability-duplexMode: int-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## minMargin

```TypeScript
minMargin?: PrintMargin
```

表示打印机最小边距。

**类型：** PrintMargin

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterCapability-minMargin?: PrintMargin--><!--Device-PrinterCapability-minMargin?: PrintMargin-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## options

```TypeScript
options?: Object
```

表示JSON对象字符串。

**类型：** Object

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-PrinterCapability-options?: Object--><!--Device-PrinterCapability-options?: Object-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## pageSize

```TypeScript
pageSize: Array<PrintPageSize>
```

表示打印机支持的页面尺寸列表。

**类型：** Array&lt;PrintPageSize&gt;

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterCapability-pageSize: Array<PrintPageSize>--><!--Device-PrinterCapability-pageSize: Array<PrintPageSize>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

## resolution

```TypeScript
resolution?: Array<PrintResolution>
```

表示打印机支持的分辨率列表。

**类型：** Array&lt;PrintResolution&gt;

**起始版本：** 24

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-PrinterCapability-resolution?: Array<PrintResolution>--><!--Device-PrinterCapability-resolution?: Array<PrintResolution>-End-->

**系统能力：** SystemCapability.Print.PrintFramework

